---
layout: default
title: Actividades del Curso
permalink: /actividades/
---

# 📝 Actividades del Curso

_Aquí encontrarás las actividades correspondientes a cada sesión del curso. Las hemos organizado de dos maneras para facilitar tu acceso._

---

## 1. Listado Secuencial de Actividades

Esta sección presenta las actividades de forma simple, numeradas secuencialmente.

{% assign sorted_sessions = site.session_metadata | sort: "order" %}

<ul class="activity-list"> 
  {% for session in sorted_sessions %}
    {% assign session_number_padded = session.order | prepend: "00" | slice: -2, 2 %}
    <li>
      <a href="{{ '/assets/activities/' | relative_url }}Actividad_S{{ session_number_padded }}.pdf"
         target="_blank"
         class="activity-link"> 
        Actividad Sesión {{ session.order }}: {{ session.title }}
      </a>
    </li>
  {% endfor %}
</ul>

---

## 2. Listado por Bloques y Sesiones

Aquí encontrarás las actividades organizadas por bloque temático, utilizando la metadata de configuración.

<div class="content-container">
  {% assign blocks_ordered = site.blocks_metadata | sort: "order" %}
  {% for block_data in blocks_ordered %}
    <div class="block-section"> 
      <h2>{{ block_data.icon }} {{ block_data.title }}</h2>
      <p class="block-description">{{ block_data.description }}</p>

      <ul class="session-list"> 
        {% for session_order_in_block in block_data.sessions %}
          {% assign numeric_session_order = session_order_in_block | plus: 0 %}
          
          {% assign found_sessions = site.session_metadata | where: "order", numeric_session_order %}
          {% assign current_session = found_sessions[0] %}

          {% if current_session %}
            {% assign session_number_padded = current_session.order | prepend: "00" | slice: -2, 2 %}
            <li class="session-item"> 
              <div class="session-header"> 
                <span class="session-order">Sesión {{ current_session.order }}</span>
                <h3>{{ current_session.title }}</h3>
              </div>
              <p class="session-description">{{ current_session.description }}</p>
              {% if current_session.obj %}
                <p class="session-objectives">Objetivos: {{ current_session.obj | join: ", " }}</p>
              {% endif %}

              <a href="{{ '/assets/activities/' | relative_url }}Actividad_S{{ session_number_padded }}.pdf"
                 target="_blank"
                 class="activity-link"> 
                Descargar Actividad
                <span class="icon">↓</span>
              </a>
            </li>
          {% endif %}
        {% endfor %}
      </ul>
    </div>
  {% endfor %}
</div>
