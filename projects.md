---
layout: page
title: Projects
permalink: /projects/
---

<ul id="project-list">
  {% assign projects = site.projects | sort: 'date' | reverse %}
  {% for project in projects %}
    <li>
      <img src="/assets/projects/{{project.short_name}}/front.jpg"/>
      <div>
        <h3><a href="{{ project.url }}">{{ project.title }}</a></h3>
        <h4>{{project.date | date: "%B %Y" }} </h4>
        <p>{{ project.description }}</p>
      </div>
    </li>
  {% endfor %}
</ul>