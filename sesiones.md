---
layout: default
title: Lista de Sesiones
permalink: /sesiones/
---

# 📅 Lista de Sesiones del Curso

_Aquí puedes encontrar todas las sesiones del curso, organizadas por bloque temático._

---

{% comment %} Convert blocks_metadata hash to an array of values and sort by 'order' {% endcomment %}
{% assign ordered_blocks = site.blocks_metadata | values | sort: "order" %} {# <-- FIX HERE! #}

{% for block_data in ordered_blocks %} {# <-- Iterate directly over block_data now #}
  {% assign block_slug = block_data.slug | default: block_data.title | slugify %} {# Fallback if slug isn't explicitly in metadata #}

  <div class="block-section">
    <h2>{{ block_data.icon }} {{ block_data.title }}</h2>
    <p>{{ block_data.description }}</p>

    <ul>
      {% comment %} Find sessions belonging to this block and sort them by 'order' {% endcomment %}
      {% assign sessions_in_block = site.sessions | where: "block", block_slug | sort: "order" %}
      {% if sessions_in_block.size > 0 %}
        {% for session in sessions_in_block %}
          <li>
            <a href="{{ session.url | relative_url }}">
              <strong>Sesión {{ session.order }}: {{ session.title }}</strong>
            </a>
            {% assign session_info = site.session_metadata[block_slug][session.slug] %}
            {% if session_info.description %}
              <br><em>{{ session_info.description }}</em>
            {% endif %}
          </li>
        {% endfor %}
      {% else %}
        <li>No hay sesiones disponibles en este bloque.</li>
      {% endif %}
    </ul>
  </div>
  <hr>
{% endfor %}
