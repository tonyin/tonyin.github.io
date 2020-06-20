---
layout: home
---


Welcome to my public site! This page I will keep updated with most of my better works, and leave the rest under different topic headings.

<div class="m-t-xl">
  <ul class="post-list">
  {%- for post in site.posts -%}
    {%- if post.tags contains 'featured' -%}
    <li>
      <h3>
        <a class="post-link" href="{{ post.url | relative_url }}">
          {{ post.title | escape }}
        </a>
      </h3>
    {{ post.excerpt }}
    </li>
    {%- endif -%}
  {%- endfor -%}
  </ul>
</div>