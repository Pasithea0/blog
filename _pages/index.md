---
layout: page
title: Home
id: home
permalink: /
---
## Welcome!

This is where I share my thoughts, ideas, and updates on my projects. 

<hr>

<strong>Recent</strong>

<ul>
  {% assign recent_notes = site.notes | sort: "last_modified_at" | reverse %}
  {% for note in recent_notes limit: 5 %}
    <li>
      <a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a>
      <br>
      <p>
        <span data-date>{{ note.last_modified_at | date: "%B&#8203; %d, %Y" }}</span> ·
        {{ note.content | reading_time }} read
      </p>
      {% assign words_limit = 14 %}
      {% assign words_count = note.content | number_of_words %}
      {% if words_count > words_limit %}
        <p>{{ note.content | strip_html | split: " " | slice: 0, words_limit | join: " " }}...
        <a class="internal-link read-more" href="{{ note.url }}">Keep reading →</a>
        </p>
      {% else %}
        <p>{{ note.content }}
        <a class="internal-link read-more" href="{{ note.url }}">Keep reading →</a>
        </p>
      {% endif %}
    </li>
    <hr> <!-- Divider -->
  {% endfor %}
</ul>

<style>
  .wrapper {
    max-width: 46em;
  }
</style>
