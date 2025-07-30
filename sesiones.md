---
layout: default
title: Sesiones del Curso
permalink: /sesiones/
---

<div class="sessions-list-container">
  <header class="sessions-list-header">
    <h1>Sesiones del Curso: {{ site.title }}</h1>
    <p class="subtitle">Explora cada una de las sesiones de este curso.</p>
  </header>

  <section class="course-objectives-summary">
    <h2>Objetivos Generales del Curso</h2>
    <ul>
      {% for obj in site.course.objectives %}
        <li>{{ obj }}</li>
      {% endfor %}
    </ul>
  </section>

  {% assign sorted_blocks = site.blocks_metadata | sort: "order" %}

  {% for block in sorted_blocks %}
    <section class="session-block">
      <h2 class="block-title">{{ block.icon }} {{ block.title }}</h2>
      <p class="block-description">{{ block.description }}</p>
      <div class="block-sessions-grid">
        {% assign block_sessions = block.sessions | sort %}
        {% for session_order in block_sessions %}
          {% assign current_session = site.sessions | where: "order", session_order | first %}
          {% if current_session %}
            <div class="session-card">
              <h3>
                <a href="{{ current_session.url | relative_url }}">
                  Sesión {{ current_session.order }}: {{ current_session.title }}
                </a>
              </h3>
              <p>{{ current_session.description }}</p>
              <ul class="session-objectives-list">
                {% if current_session.obj %}
                  {% for obj in current_session.obj limit: 3 %}
                    <li>{{ obj }}</li>
                  {% endfor %}
                  {% if current_session.obj.size > 3 %}
                    <li>... y más</li>
                  {% endif %}
                {% endif %}
              </ul>
              <a href="{{ current_session.url | relative_url }}" class="button button-secondary">Ver Sesión →</a>
            </div>
          {% endif %}
        {% endfor %}
      </div>
    </section>
  {% endfor %}
</div>
