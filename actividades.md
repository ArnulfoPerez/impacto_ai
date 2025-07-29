---
layout: default
title: Actividades del Curso
permalink: /actividades/
---

# ✍️ Actividades del Curso

_Aquí encontrarás todas las actividades prácticas y ejercicios propuestos para cada sesión del curso. Hemos organizado las actividades de dos maneras para facilitar su acceso._

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

{% assign max_session_order = 8 %} {# Valor predeterminado a 8 #}
{% if valid_session_orders.size > 0 %}
  {% assign calculated_max = valid_session_orders | max %}
  {% if calculated_max > max_session_order %}
    {% assign max_session_order = calculated_max %} {# Usar el máximo calculado si es mayor que 8 #}
  {% endif %}
{% endif %}


## 1. Listado Secuencial de Actividades (1 a {{ max_session_order }})

Esta sección presenta las actividades de forma simple, numeradas secuencialmente. Son ideales si el usuario ya sabe qué actividad busca por su número de sesión.

<ul>
{% for i in (1..max_session_order) %}
    {% assign session_number_padded = i | prepend: "0" | slice: -2, 2 %}
    {% comment %} Corrected link generation for baseurl compatibility {% endcomment %}
    <li><a href="{{ site.baseurl }}/assets/activities/Actividad_S{{ session_number_padded }}.pdf" target="_blank">Actividad de la sesión {{ i }}</a></li>
{% endfor %}
</ul>

---

## 2. Listado Descriptivo por Bloque y Sesión

Esta sección organiza las actividades en función de los bloques y sesiones del curso, proporcionando un contexto más rico. Es perfecta para quienes quieren entender la ubicación de la actividad dentro de la estructura del curso.

{% assign sorted_sessions = site.sessions | sort: 'order' %}
{% assign blocks = sorted_sessions | group_by: 'block' %}

{% for block in blocks %}
### {{ block.name }}

<ul>
    {% for session in block.items %}
    {% comment %} Mostramos actividades solo para las sesiones hasta el número máximo dinámico o 8 {% endcomment %}
    {% if session.order != null and session.order != "" and session.order <= max_session_order %}
        <li>
            <a href="{{ session.url | relative_url }}">**{{ session.title }}**</a>
            <ul>
                {% assign session_number_padded = session.order | prepend: "0" | slice: -2, 2 %}
                {% comment %} Corrected link generation for baseurl compatibility {% endcomment %}
                <li><a href="{{ site.baseurl }}/assets/activities/Actividad_S{{ session_number_padded }}.pdf" target="_blank">Actividad de la sesión {{ session.order }}</a></li>
            </ul>
        </li>
    {% endif %}
    {% endfor %}
</ul>
{% endfor %}
