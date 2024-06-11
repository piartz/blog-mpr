---
layout: default
title: "Inicio"
---

## Martin Perez Rodriguez

Apaixoado da ciberseguridade, Cloud, DevSecOps e procesos de desenvolvemento de software. Actualmente adicome á consultoría nos Países Baixos. 

### Ultimos Posts

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span>{{ post.date | date_to_string }}</span>
    </li>
  {% endfor %}
</ul>
