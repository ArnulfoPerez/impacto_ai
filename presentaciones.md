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


# 💻 Presentaciones del Curso

_Aquí encontrarás todas las presentaciones utilizadas en cada sesión del curso. Las hemos organizado de dos maneras para facilitar tu acceso._

---

## 1. Listado Secuencial de Presentaciones

Esta sección presenta las presentaciones de forma simple, numeradas secuencialmente.

{% comment %}
  site.session_metadata is now directly an array of session hashes.
  We can directly sort it by the 'order' property.
{% endcomment %}
{% assign sorted_sessions = site.session_metadata | sort: "order" %}

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

## 2. Listado por Bloques y Sesiones

Aquí encontrarás las presentaciones organizadas por bloque temático, utilizando la metadata de configuración.

<div class="presentations-container">
  {% assign blocks_ordered = site.blocks_metadata | sort: "order" %}
  {% for block_entry in blocks_ordered %}
    {% assign block_slug = block_entry[0] %}
    {% assign block_data = block_entry[1] %}

    <div class="block-section">
      <h2>{{ block_data.icon }} {{ block_data.title }}</h2>
      <p class="block-description">{{ block_data.description }}</p>
      
      <ul class="session-list">
        {% comment %}
          For each block, iterate through the session *order numbers* defined in blocks_metadata.
          Use the 'where' filter to efficiently find the corresponding session data from site.session_metadata.
        {% endcomment %}
        {% for session_order_in_block in block_data.sessions %}
          {% assign found_sessions = site.session_metadata | where: "order", session_order_in_block %}
          {% assign current_session = found_sessions[0] %} {# 'where' returns an array, take the first matching item #}

          {% if current_session %}
            {% assign session_number_padded = current_session.order | prepend: "0" | slice: -2, 2 %}
            <li class="session-item">
              <div class="session-header">
                <span class="session-order">Sesión {{ current_session.order }}</span>
                <h3>{{ current_session.title }}</h3>
              </div>
              <p class="session-description">{{ current_session.description }}</p>

              <a href="{{ '/assets/presentations/' | relative_url }}sesion_S{{ session_number_padded }}.pptx"
                 target="_blank"
                 class="presentation-link">
                Descargar presentación
                <span class="icon">↓</span>
              </a>
            </li>
          {% endif %}
        {% endfor %}
      </ul>
    </div>
  {% endfor %}
</div>

<style>
  .presentations-container {
    margin-top: 2rem;
  }
  
  .block-section {
    margin-bottom: 3rem;
    padding: 1.5rem;
    background-color: #f8f9fa;
    border-radius: 8px;
  }
  
  .block-description {
    color: #555;
    margin-bottom: 1.5rem;
  }
  
  .session-list {
    list-style: none;
    padding-left: 0;
  }
  
  .session-item {
    margin-bottom: 1.5rem;
    padding: 1rem;
    background: white;
    border-radius: 6px;
    box-shadow: 0 1px 3px rgba(0,0,0,0.1);
  }
  
  .session-header {
    display: flex;
    align-items: baseline;
    gap: 1rem;
    margin-bottom: 0.5rem;
  }
  
  .session-order {
    font-weight: bold;
    color: #2c3e50;
  }
  
  .session-description {
    color: #444;
    margin: 0.5rem 0;
  }
  
  .presentation-link {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.5rem 1rem;
    background-color: #0366d6;
    color: white;
    text-decoration: none;
    border-radius: 4px;
    transition: background-color 0.2s;
  }
  
  .presentation-link:hover {
    background-color: #0056b3;
  }
  
  .icon {
    font-size: 0.9em;
  }
</style>
