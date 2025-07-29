---
layout: default
title: Presentaciones del Curso
permalink: /presentaciones/
---
 
# 💻 Presentaciones del Curso

_Aquí encontrarás todas las presentaciones utilizadas en cada sesión del curso. Las hemos organizado de dos maneras para facilitar tu acceso._

---

{% comment %} Obtener el número máximo de sesiones para el bucle.
   Si no se encuentran sesiones o sus órdenes, se usará 8 como valor predeterminado.
{% endcomment %}
{% assign all_session_orders = site.sessions | map: "order" %}

{% comment %} Filtrar valores nulos o vacíos antes de encontrar el máximo {% endcomment %}
{% assign valid_session_orders = "" | split: "," %}
{% for order_val in all_session_orders %}
  {% if order_val != null and order_val != "" %}
    {% assign valid_session_orders = valid_session_orders | push: order_val %}
  {% endif %}
{% endfor %}

{% assign max_session_order = 8 %}
{% if valid_session_orders.size > 0 %}
  {% assign calculated_max = valid_session_orders | max %}
  {% if calculated_max > max_session_order %}
    {% assign max_session_order = calculated_max %} {# Usar el máximo calculado si es mayor que 8 #}
  {% endif %}
{% endif %}


## 1. Listado Secuencial de Presentaciones (1 a {{ max_session_order }})

Esta sección presenta las presentaciones de forma simple, numeradas secuencialmente. Son ideales si el usuario ya sabe qué presentación busca por su número de sesión.

<ul class="activity-list">
  {% for i in (1..8) %}
    {% assign session_number_padded = i | prepend: "00" | slice: -2, 2 %}
    <li>
      <a href="{{ '/assets/presentaciones/' | relative_url }}sesion_S{{ session_number_padded }}.pptx" 
         target="_blank" 
         class="activity-link">
        Actividad Sesión {{ i }}
      </a>
    </li>
  {% endfor %}
</ul>
