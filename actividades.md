---
layout: default
title: Presentaciones del Curso
permalink: /actividades/
---

# 💻 Actividades del Curso

_Aquí encontrarás todas las presentaciones utilizadas en cada sesión del curso. Las hemos organizado de dos maneras para facilitar tu acceso._

---

## 1. Listado Secuencial de Presentaciones (1 a 8)

Esta sección presenta las presentaciones de forma simple, numeradas secuencialmente. Son ideales si el usuario ya sabe qué presentación busca por su número de sesión.

<ul class="activity-list">
  {% for i in (1..8) %}
    {% assign session_number_padded = i | prepend: "00" | slice: -2, 2 %}
    <li>
      <a href="{{ '/assets/activities/' | relative_url }}Actividades_S{{ session_number_padded }}.pdf" 
         target="_blank" 
         class="activity-link">
        Actividad Sesión {{ i }}
      </a>
    </li>
  {% endfor %}
</ul>
