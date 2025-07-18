---
layout: default
title: Actividades del curso
---

# 🧠 Actividades disponibles

<ul>
  {% assign actividades = site.pages | where_exp:"p","p.url contains '/actividades/' and p.title" %}
  {% for actividad in actividades %}
    <li><a href="{{ actividad.url | relative_url }}">{{ actividad.title }}</a></li>
  {% endfor %}
</ul>
