---
layout: page
title: Projects
permalink: /projects/
---

This will be the projects page!

<ul>
  {% for project in site.projects %}
    <li>
      <h2><a href="{{ project.url }}">{{ project.title }}</a></h2>
    </li>
  {% endfor %}
</ul>