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
  {% for i in (1..8) %}
    {% assign session_number_padded = i | prepend: "00" | slice: -2, 2 %}
    <li>
      <a href="{{ '/assets/activities/' | relative_url }}Actividad_S{{ session_number_padded }}.pdf" 
         target="_blank" 
         class="activity-link">
        Actividad Sesión {{ i }}
      </a>
    </li>
  {% endfor %}
</ul>
----
