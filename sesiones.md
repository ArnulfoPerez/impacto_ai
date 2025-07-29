---
layout: default
title: Lista de sesiones
permalink: /sesiones/
---

# 📅 Lista de Sesiones del Curso

_Aquí puedes encontrar todas las sesiones del curso, organizadas por bloque temático._

---

{% assign blocks = site.blocks_metadata | sort: "order" %}

{% for block in blocks %}
  {% assign block_slug = block[0] %}
  {% assign block_data = block[1] %}

  <div class="block-section">
    <h2>{{ block_data.icon }} {{ block_data.title }}</h2>
    <p>{{ block_data.description }}</p>

    <ul>
      {% assign sessions_in_block = site.sessions | where: "block", block_slug | sort: "order" %}
      {% if sessions_in_block.size > 0 %}
        {% for session in sessions_in_block %}
          <li>
            <a href="{{ session.url | relative_url }}">
              <strong>Sesión {{ session.order }}: {{ session.title }}</strong>
            </a>
            {% if session.description %}
              <br><em>{{ session.description }}</em>
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
