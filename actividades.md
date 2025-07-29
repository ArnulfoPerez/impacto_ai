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

## 2. Listado Descriptivo por Bloque Temático

Esta sección organiza las actividades por bloques del curso, proporcionando contexto sobre su ubicación en la estructura del curso.

{% assign blocks = site.sessions | group_by: "block" | sort: "name" %}

{% for block in blocks %}
  <div class="activity-block">
    <h3>{{ site.blocks_metadata[block.name].title | default: block.name }}</h3>
    <p class="block-description">{{ site.blocks_metadata[block.name].description }}</p>
    
    <ul class="block-sessions">
    {% for session in block.items | sort: "order" %}
      {% if session.order %}
        {% assign session_number_padded = session.order | prepend: "00" | slice: -2, 2 %}
        <li class="session-item">
          <div class="session-header">
            <span class="session-order">Sesión {{ session.order }}</span>
            <a href="{{ session.url | relative_url }}" class="session-title">{{ session.title }}</a>
          </div>
          <a href="{{ '/assets/activities/' | relative_url }}Actividad_S{{ session_number_padded }}.pdf" target="_blank" class="activity-link">
            Descargar actividad
            <span class="activity-icon" aria-hidden="true">↓</span>
          </a>
        </li>
      {% endif %}
    {% endfor %}
    </ul>
  </div>
{% endfor %}

<style>
  .activity-list, .block-sessions {
    list-style: none;
    padding-left: 0;
  }
  
  .activity-link {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.5rem 0;
    text-decoration: none;
    color: #0366d6;
  }
  
  .activity-link:hover {
    text-decoration: underline;
  }
  
  .activity-icon {
    font-size: 0.8em;
  }
  
  .activity-block {
    margin-bottom: 2rem;
    padding: 1rem;
    background-color: #f6f8fa;
    border-radius: 6px;
  }
  
  .block-description {
    color: #586069;
    margin-top: 0.5rem;
  }
  
  .session-item {
    margin-bottom: 1rem;
    padding: 0.75rem;
    background: white;
    border-radius: 4px;
    box-shadow: 0 1px 3px rgba(0,0,0,0.1);
  }
  
  .session-header {
    margin-bottom: 0.5rem;
  }
  
  .session-order {
    font-weight: bold;
    margin-right: 0.5rem;
  }
</style>
