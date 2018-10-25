---
layout: post
title: Freeform Coding
date: '2015-10-18 05:42:59'
tags:
- ideas
- code
---

I’ve been thinking of a new text editing / interactive development environment concept. It is somewhat inspired by OneNote, which I just had to Google and see what it was like. Side note: Microsoft (actually many tech companies) are really into using real-life people doing real-life things as backdrops for advertising their wares. I remember OneNote allows you to click and drag, creating a text box anywhere in the note-taking page to create a new snippet. This felt very free to me as I had always been constrained to the line-by-line environments on the computer.

I have yet to see anything revolutionary and substantial in terms of IDEs. Almost everything uses the same top-to-bottom left-to-right writing paradigm that has existed since computers have existed. That’s decades and decades. Why has there been nothing new? Perhaps I am crazy and there is nothing to improve on. Or maybe I’m onto something.

My idea is to allow click and drag text boxes anywhere within your IDE to create code blocks. The code blocks can then be ordered to execute in parallel or in sequence depending on your needs. At LinkedIn, we use Azkaban, an open source job scheduler, to execute jobs in parallel or in sequence based on instructions from a gradle file, and the visualization is similar to what I envision. This new coding paradigm is more flexible and intuitive to break down code and take advantage of faster processing power, not to mention larger screen real estate.

The UI will have to be done very carefully. I can easily see this idea failing because of a poor UI that makes it too messy for the user to see what is going on. There should also be a “reorder” command that collapses the code into in-sequence form to ease the transition to this new paradigm.

Graph visualization + code. Graphcode. Codegraph.