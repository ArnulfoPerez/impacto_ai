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

<ul>
  {% for i in (1..8) %}
    {% assign session_num = i | prepend: '00' | slice: -2, 2 %}
    <li>
      <a href="{{ site.baseurl }}/assets/activities/Actividad_S{{ session_num }}.pdf" target="_blank">Actividad de la sesión {{ i }}</a>
    </li>
  {% endfor %}
</ul>
