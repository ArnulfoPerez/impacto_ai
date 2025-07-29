---
layout: default
title: Presentaciones del Curso
permalink: /presentaciones/
---

# 💻 Presentaciones del Curso

_Aquí encontrarás todas las presentaciones utilizadas en cada sesión del curso. Las hemos organizado de dos maneras para facilitar tu acceso._

---

{% comment %} Obtener el número máximo de sesiones para el bucle {% endcomment %}
{% assign all_session_orders = site.sessions | map: "order" %}
{% assign max_session_order = all_session_orders | max %}

## 1. Listado Secuencial de Presentaciones (1 a {{ max_session_order }})

Esta sección presenta las presentaciones de forma simple, numeradas secuencialmente. Son ideales si el usuario ya sabe qué presentación busca por su número de sesión.

<ul>
{% for i in (1..max_session_order) %}
    {% assign session_number_padded = i | prepend: "0" | slice: -2, 2 %}
    <li><a href="/assets/presentations/Sesion_S{{ session_number_padded }}.pptx" target="_blank">Presentación de la sesión {{ i }}</a></li>
{% endfor %}
</ul>

---

## 2. Listado Descriptivo por Bloque y Sesión

Esta sección organiza las presentaciones en función de los bloques y sesiones del curso, proporcionando un contexto más rico. Es perfecta para quienes quieren entender la ubicación de la presentación dentro de la estructura del curso.

{% assign sorted_sessions = site.sessions | sort: 'order' %}
{% assign blocks = sorted_sessions | group_by: 'block' %}

{% for block in blocks %}
### {{ block.name }}

<ul>
    {% for session in block.items %}
    {% comment %} Mostramos presentaciones solo para las sesiones hasta el número máximo encontrado {% endcomment %}
    {% if session.order <= max_session_order %}
        <li>
            <a href="{{ session.url | relative_url }}">**{{ session.title }}**</a>
            <ul>
                {% assign session_number_padded = session.order | prepend: "0" | slice: -2, 2 %}
                <li><a href="/assets/presentations/Sesion_S{{ session_number_padded }}.pptx" target="_blank">Presentación de la sesión {{ session.order }}</a></li>
            </ul>
        </li>
    {% endif %}
    {% endfor %}
</ul>
{% endfor %}
