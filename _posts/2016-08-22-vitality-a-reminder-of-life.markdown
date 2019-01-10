---
layout: post
title: Vitality - A reminder of life
image: "/assets/img/2017/01/screenshot_web.jpg"
date: '2016-08-22 05:55:35'
tags:
- extension
- chrome
- howto
- code
---

tl;dr - [Chrome extension](https://chrome.google.com/webstore/detail/vitality/ofnbjjlogningakpjgphhiidgkbjgcch) that reminds you of the years flowing by with every new tab.

![screenshot](/assets/img/2016/08/screenshot_web.jpg)

## Motivation

We can only systematically improve what we can measure. This belief is canon in business - every objective will have "key performance indicators" or “true north metrics” that reflect how well we are executing against that objective. Without metrics, we operate blindly albeit intuitively. The best solutions combine both metrics and intuition together for a data-driven, intuition-guided approach.

I believe we severely lack the data-driven aspect in our personal lives. To-do lists and bodyweight scales are the extent of measuring anything about ourselves. Step-counting has also hit the mainstream thanks to the Fitbit, smartphone accelerometers, and smartwatches, but they are underutilized even so.

The bulk of this post is about a Chrome extension called [Vitality](https://chrome.google.com/webstore/detail/vitality/ofnbjjlogningakpjgphhiidgkbjgcch) that I made last weekend. I was inspired by a quantified self dashboard called [Gyroscope](https://gyrosco.pe/) that has an unusual way of displaying your age in decimal notation with 9 significant figures, or billionth of a year. Nine significant figures is just fast enough that the flow of time is too fast for our visual perception of individual time increments, ie. the 0-1-2-3-x changes are too fast for us to see individually. This timer effect prompts a jumble of feelings, but most of all, it prompts a feeling of urgency. It makes me think “wow, the years and time pass so quickly”. Vitality takes that age visualization and displays it front and center. When used correctly, Vitality reminds us of the years flowing by with every new tab (potential distraction) and creates a sense of urgency to live life. We all could use a reminder that our year number is only getting bigger.

## Development

Github link: https://github.com/tonyin/vitality

The official Chrome [Getting Started](https://developer.chrome.com/extensions/getstarted) docs is a good place to start. Create the following files:

- `manifest.json`
- `app.html`
- `app.js`
- `app.css`

`manifest.json` declares the basic metadata and permissions. There are many [sample files](https://developer.chrome.com/extensions/samples) that you can use as a starting template.
```language-json
{
  "manifest_version": 2,
  "name": "Vitality",
  "description": "Life flows from one moment to the next. Remember your vitality with each new tab.",
  "version": "0.0.2",
  "browser_action": {
    "default_icon": "icon.png"
  },
  "chrome_url_overrides": {
    "newtab": "app.html"
  },
  "permissions": [
    "storage",
    "https://www.google-analytics.com/"
  ]
}
```

`app.html` holds the new tab html and scripts. Style the page with `app.css` and run scripts with `app.js`.

```language-html
<!doctype html>
<html>
  <head>
    <title>New Tab</title>
    <link type="text/css" rel="stylesheet" href="app.css" />
  </head>
  <body>
    <div class="container"></div>
    <script type="text/javascript" src="jquery-3.1.0.min.js"></script>
    <script type="text/javascript" src="app.js"></script>
  </body>
</html>
```

`app.js` holds most of the program logic.

```language-javascript
document.addEventListener('DOMContentLoaded', function() {
  createVitalityDisplay();
  ...
};
```

After the new tab page boots up (but before scripts and such are loaded), `DOMContentLoaded`, kick off a `createVitalityDisplay` function.

```language-javascript
function createVitalityDisplay() {
  var vitWrapper = document.createElement("div");
  vitWrapper.setAttribute('id', "vit-wrapper");
  vitWrapper.setAttribute('align', "center");

  var vitText1 = document.createElement("p");
  vitText1.innerHTML = "YOU ARE";
  vitWrapper.appendChild(vitText1);

  var vit = document.createElement("span");
  vit.setAttribute('id', "vitality");
  vitWrapper.appendChild(vit);

  var vitText2 = document.createElement("p");
  vitText2.innerHTML = "YEARS OLD";
  vitWrapper.appendChild(vitText2);

  document.getElementsByClassName('container')[0].appendChild(vitWrapper);
  vitWrapper.style.display = "none"; // hide for now
};
```

“VitalityDisplay” is the main age visualization, displaying “YOU ARE”, a holder span element for the timer, and “YEARS OLD”. After it is created, it is hidden in case the user has not input their birthdate yet.

```language-javascript
document.addEventListener('DOMContentLoaded', function() {
  createVitalityDisplay();

  // use stored birthdate if already entered
  chrome.storage.local.get('birthdate', function(data) {
    if (data.birthdate > 0) {
      startVitality(data.birthdate);
    } else {
      createBirthdateForm();
      handleBirthdateForm();
    };
  });
});
```

After creating the “VitalityDisplay”, check if the user has already input and stored their birthdate. `chrome.storage.local` uses local storage (as opposed to cloud storage) to keep birthdate data only on local device premise. The script calls “startVitality” if a birthdate is found, otherwise it creates a “BirthdateForm” and listens for input from “BirthdateForm”.

```language-javascript
function createBirthdateForm () {
  var bWrapper = document.createElement("div");
  bWrapper.setAttribute('id', "b-wrapper");
  bWrapper.setAttribute('align', "center");

  var f = document.createElement("form");
  f.setAttribute('method', "post");
  f.setAttribute('id', 'birthdateForm');
  f.setAttribute('align', "center");
  f.setAttribute('display', "block");

  var bdate = document.createElement("input");
  bdate.setAttribute('name', "bdate");
  bdate.setAttribute('required', '');
  bdate.setAttribute('type', "date");
  // bdate.setAttribute('value', "1989-06-14");
  bdate.setAttribute('class', "unstyled");

  var btn = document.createElement("input");
  btn.setAttribute('type', "submit");
  btn.setAttribute('value', ">>");

  f.appendChild(bdate);
  f.appendChild(btn);
  bWrapper.appendChild(f);

  var bText = document.createElement("p");
  bText.innerHTML = "BIRTHDATE";
  bWrapper.appendChild(bText);

  document.getElementsByClassName('container')[0].appendChild(bWrapper);
};

function handleBirthdateForm() {
  var birthdateForm = document.getElementById('birthdateForm');
  if (birthdateForm.attachEvent) {
    birthdateForm.attachEvent("submit", saveBirthdate);
  } else {
    birthdateForm.addEventListener("submit", saveBirthdate);
  };
};
```

Standard form creation, display, and submit handling. On submit, “saveBirthdate” is called which uses `chrome.storage.local` mentioned earlier to save the birthdate data.

```language-javascript
function saveBirthdate(e) {
  if (e.preventDefault) e.preventDefault();

  var bWrapper = $('#b-wrapper');
  var birthdate = document.getElementById('birthdateForm').elements[0].valueAsNumber;
  bWrapper.fadeOut('fast');

  // save
  chrome.storage.local.set({
    'birthdate': birthdate
  });
  startVitality(birthdate);
};
```

After the birthdate is saved, use jQuery to hide the form and start the Vitality display.

```language-javascript
function startVitality(birthdate) {
  var vit = document.getElementById('vitality');

  // start timer
  var interval = setInterval(function() {
    var currentVit = (Date.now() - birthdate) / (365*24*60*60*1000);
    vit.innerHTML = currentVit.toFixed(9);
  }, 50);

  ...

  // delay slightly for ux
  setTimeout(function() {
    document.getElementById('vit-wrapper').style.display = "block"; // show
    document.body.appendChild(reset);
  }, 400);
};
```

The age visualization uses `setInterval` to calculate, every 50 ms, the difference between the current time and the user’s birthdate in years with 9 significant digits.

```language-javascript
function startVitality(birthdate) {
  ...

  // add reset button
  var reset = document.createElement("span");
  reset.setAttribute('id', "reset");
  reset.innerHTML = "reset";
  if (reset.attachEvent) {
    reset.attachEvent("click", handleReset);
  } else {
    reset.addEventListener("click", handleReset);
  };

  ...
};

function handleReset() {
  chrome.storage.local.remove('birthdate', function() {
    location.reload();
  });
};
```

And include a “reset” button to allow the user to change the birthdate if they so choose. “Reset" is induced by removing the locally stored birthdate data and reloading the page.

Load using `chrome://extensions` for fast change/reload development.

Package extension using `chrome://extensions` to get an initial `.pem` file. Keep that file secure and out of version control.

Pay $5 to publish in the Chrome store.

Update extension by copying the `.pem` file into the extension directory as `key.pem`, incrementing the version number in `manifest.json`, zipping the directory through the command line (like `zip -r vitality.zip vitality -x *.git*`), and uploading through the Chrome web dashboard.

Profit (???)