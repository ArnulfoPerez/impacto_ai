---
layout: default
title: Presentaciones del Curso
permalink: /presentaciones/
---

# 💻 Presentaciones del Curso

_Aquí encontrarás todas las presentaciones utilizadas en cada sesión del curso. Las hemos organizado de dos maneras para facilitar tu acceso._

---

## 1. Listado Secuencial de Presentaciones (1 a 8)

Esta sección presenta las presentaciones de forma simple, numeradas secuencialmente. Son ideales si el usuario ya sabe qué presentación busca por su número de sesión.

<ul class="activity-list">
  {% for i in (1..8) %}
    {% assign session_number_padded = i | prepend: "00" | slice: -2, 2 %}
    <li>
      <a href="{{ '/assets/presentations/' | relative_url }}sesion_S{{ session_number_padded }}.pptx" 
         target="_blank" 
         class="activity-link">
        Presentación Sesión {{ i }}
      </a>
    </li>
  {% endfor %}
</ul>

---


{% comment %}
  Flatten all session metadata into a single array and sort by 'order'.
  This avoids issues with nested hashes when sorting across blocks.
{% endcomment %}
{% assign flat_sessions = "" | split: "" %}
{% for block_key in site.session_metadata %}
  {% assign block_sessions = block_key[1] | values %}
  {% assign flat_sessions = flat_sessions | concat: block_sessions %}
{% endfor %}
{% assign sorted_sessions = flat_sessions | sort: "order" %}

<ul class="activity-list">
  {% for session in sorted_sessions %}
    {% assign session_number_padded = session.order | prepend: "0" | slice: -2, 2 %}
    <li>
      <a href="{{ '/assets/presentations/' | relative_url }}sesion_S{{ session_number_padded }}.pptx"
         target="_blank"
         class="activity-link">
        Presentación Sesión {{ session.order }}: {{ session.title }}
      </a>
    </li>
  {% endfor %}
</ul>

---
