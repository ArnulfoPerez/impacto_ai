---
layout: default
title: Lista de Sesiones
permalink: /sesiones/
---

# 📅 Lista de Sesiones del Curso

_Aquí puedes encontrar todas las sesiones del curso, organizadas por bloque temático._

---

{% comment %} Sort blocks_metadata by the 'order' property {% endcomment %}
{% assign ordered_blocks = site.blocks_metadata | sort: "1.order" %}

{% for block_slug_pair in ordered_blocks %}
  {% assign block_slug = block_slug_pair[0] %}
  {% assign block_data = block_slug_pair[1] %}

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
