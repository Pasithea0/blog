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
  {% assign recent_notes = site.notes | sort: "date" | reverse %}
  {% for note in recent_notes limit: 5 %}
    <li>
      <a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a>
      <br>
      <p>
        {% assign day = note.date | date: "%-d" %}
        {% assign month = note.date | date: "%B" %}
        {% assign year = note.date | date: "%Y" %}
        <span data-date>{{ month }}&#8203; {{ day }}&#8203;, {{ year }}</span> ·
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
