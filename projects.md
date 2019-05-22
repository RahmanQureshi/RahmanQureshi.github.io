---
layout: page
title: Projects
permalink: /projects/
---

<ul id="project-list">
  {% for project in site.projects %}
    <li>
      <img src="/assets/projects/{{project.short_name}}/front.jpg"/>
      <div>
        <h2><a href="{{ project.url }}">{{ project.title }}</a></h2>
        <p>{{ project.description }}</p>
      </div>
    </li>
  {% endfor %}
</ul>