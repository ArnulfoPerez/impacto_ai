---
layout: default
title: Sesiones del Curso
permalink: /sesiones/
---

<div class="list-container"> {# Consolidated: Replaced sessions-list-container with list-container #}
  <header class="list-page-header"> {# Consolidated: Replaced sessions-list-header with list-page-header #}
    <h1>Sesiones del Curso: {{ site.title }}</h1>
    <p class="subtitle" >Explora cada una de las sesiones de este curso.</p>
  </header>

  <section class="block-section"> {# This section wraps the course objectives as a distinct block #}
    <h2>Objetivos Generales del Curso</h2>
    <ul>
      {% for obj in site.course.objectives %}
        <li>{{ obj }}</li>
      {% endfor %}
    </ul>
  </section>

  {% assign sorted_blocks = site.blocks_metadata | sort: "order" %}

  {% for block in sorted_blocks %}
    <section class="block-section"> {# Consolidated: Replaced session-block with block-section #}
      <h2 class="block-title">{{ block.icon }} {{ block.title }}</h2>
      <p class="block-description">{{ block.description }}</p>
      <div class="item-grid"> {# Consolidated: Replaced block-sessions-grid with item-grid #}
        {% assign block_sessions = block.sessions | sort %}
        {% for session_order in block_sessions %}
          {% assign current_session = site.sessions | where: "order", session_order | first %}
          {% if current_session %}
            <div class="item-card"> {# Consolidated: Replaced session-card with item-card #}
              <h3 class="item-title"> {# Consolidated: Replaced h3 with item-title #}
                <a href="{{ current_session.url | relative_url }}">
                  Sesión {{ current_session.order }}: {{ current_session.title }}
                </a>
              </h3>
              <p class="item-description">{{ current_session.description }}</p> {# Consolidated: Added item-description #}
              
              {# Session objectives list #}
              <ul class="item-list"> {# Consolidated: Replaced session-objectives-list with item-list #}
                {% if current_session.obj %}
                  {% for obj in current_session.obj limit: 3 %}
                    <li class="list-item">{{ obj }}</li> {# Consolidated: Added list-item #}
                  {% endfor %}
                  {% if current_session.obj.size > 3 %}
                    <li class="list-item">... y más</li>
                  {% endif %}
                {% endif %}
              </ul>

              {# Session Resources #}
              <h3>Recursos de la Sesión</h3>
              <ul class="page-links-list"> {# Consolidated: Replaced session-page-links with page-links-list #}
                {% assign session_number_padded = session_order | prepend: "00" | slice: -2, 2 %}
                <li>
                  <a href="{{ '/assets/presentations/' | relative_url }}sesion_S{{ session_number_padded }}.pptx"
                    target="_blank"
                    class="resource-button resource-button--primary"> {# Consolidated: Used resource-button classes #}
                    Descargar Presentación <span class="icon">↓</span>
                  </a>
                </li>
                <li>
                  <a href="{{ '/assets/activities/' | relative_url }}Actividad_S{{ session_number_padded }}.pdf"
                    target="_blank"
                    class="resource-button resource-button--success"> {# Consolidated: Used resource-button classes #}
                    Descargar Actividad <span class="icon">↓</span>
                  </a>
                </li>
                {# Assuming additional_links might come from session.additional_links, not block's #}
                {% if current_session.additional_links %}
                  {% for link in current_session.additional_links %}
                    <li>
                      <a href="{{ link.url | relative_url }}" target="_blank" class="resource-button resource-button--secondary">
                        {{ link.title }} <span class="icon">↗</span>
                      </a>
                    </li>
                  {% endfor %}
                {% endif %}
              </ul>
              
              <div class="item-actions"> {# Added wrapper for consistency #}
                <a href="{{ current_session.url | relative_url }}" class="button button-secondary">Ver Sesión →</a>
              </div>
            </div>
          {% endif %}
        {% endfor %}
      </div>
    </section>
  {% endfor %}
</div>
