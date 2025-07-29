---
layout: default
title: Sesiones del Curso
permalink: /sesiones/
---

# 📅 Sesiones del Curso

_Aquí encontrarás todas las sesiones del curso, organizadas por bloque temático, ofreciendo una visión detallada de cada módulo._

---

<div class="session-list">
    {% assign sorted_block_keys = site.blocks_metadata | map: "first" | sort %} {# Ordena los bloques para mostrar consistentemente #}
    {% for block_slug in sorted_block_keys %}
        {% assign block_data = site.blocks_metadata[block_slug] %}

        <h2>{{ block_data.icon }} {{ block_data.title }}</h2>
        <p>{{ block_data.description }}</p>

        {% assign sessions_in_block = site.sessions | where: "block", block_slug | sort: "order" %}

        {% if sessions_in_block.size > 0 %}
            <ul>
                {% for session in sessions_in_block %}
                    {% assign session_slug = session.slug %}
                    {% assign session_details = site.session_metadata[block_slug][session_slug] %}
                    <li>
                        <a href="{{ session.url | relative_url }}">
                            <strong>Sesión {{ session.order }}: {{ session_details.title | default: session.title }}</strong>
                        </a>
                        {% if session_details.obj %}
                            <br>Objetivos:
                            <ul>
                                {% for obj in session_details.obj %}
                                    <li>{{ obj }}</li>
                                {% endfor %}
                            </ul>
                        {% endif %}
                        {% if session_details.description %}
                            <p>_Descripción: {{ session_details.description }}_</p>
                        {% endif %}
                    </li>
                {% endfor %}
            </ul>
        {% else %}
            <p>No hay sesiones definidas para este bloque aún.</p>
        {% endif %}
    {% endfor %}
</div>
