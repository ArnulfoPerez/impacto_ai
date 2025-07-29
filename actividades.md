---
layout: default
title: Actividades del Curso
permalink: /actividades/
---

# ✍️ Actividades del Curso

_Aquí encontrarás todas las actividades prácticas y ejercicios propuestos para cada sesión del curso. Hemos organizado las actividades de dos maneras para facilitar su acceso._

---

## 1. Listado Secuencial de Actividades

Esta sección presenta las actividades de forma simple, numeradas secuencialmente. Ideal si ya sabes qué actividad buscas por su número de sesión.

<ul class="activity-list">
{% for session in site.sessions | sort: "order" %}
  {% if session.order %}
    {% assign session_number_padded = session.order | prepend: "00" | slice: -2, 2 %}
    <li>
      <a href="{{ '/assets/activities/' | relative_url }}Actividad_S{{ session_number_padded }}.pdf" target="_blank" class="activity-link">
        <span class="session-number">Sesión {{ session.order }}:</span>
        <span class="activity-title">{{ session.title }}</span>
        <span class="activity-icon" aria-hidden="true">↗</span>
      </a>
    </li>
  {% endif %}
{% endfor %}
</ul>

---
