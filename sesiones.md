---
layout: default
title: Sesiones del Curso
permalink: /sesiones/
---

<div class="list-container"> 
  <header class="list-page-header"> 
    <h1>Sesiones del Curso: {{ site.title }}</h1>
    <p class="subtitle" >Explora cada una de las sesiones de este curso.</p>
  </header>

  <section class="block-section"> 
    <h2>Objetivos Generales del Curso</h2>
    <ul>
      {% for obj in site.course.objectives %}
        <li>{{ obj }}</li>
      {% endfor %}
    </ul>
  </section>

  {% assign sorted_blocks = site.blocks_metadata | sort: "order" %}

  {% for block in sorted_blocks %}
    <section class="block-section"> 
      <h2 class="block-title">{{ block.icon }} {{ block.title }}</h2>
      <p class="block-description">{{ block.description }}</p>
      <div class="item-grid"> 
        {% assign block_sessions = block.sessions | sort %}
        {% for session_order in block_sessions %}
          {% assign current_session = site.sessions | where: "order", session_order | first %}
          {% if current_session %}
            <div class="item-card"> 
              <h3 class="item-title"> 
                <a href="{{ current_session.url | relative_url }}">
                  Sesión {{ current_session.order }}: {{ current_session.title }}
                </a>
              </h3>
              <p class="item-description">{{ current_session.description }}</p> 
              
              {# Session objectives list #}
              <ul class="item-list"> 
                {% if current_session.obj %}
                  {% for obj in current_session.obj limit: 3 %}
                    <li class="list-item">{{ obj }}</li> 
                  {% endfor %}
                  {% if current_session.obj.size > 3 %}
                    <li class="list-item">... y más</li>
                  {% endif %}
                {% endif %}
              </ul>

              <h3>Recursos de la Sesión</h3>
              <ul class="page-links-list"> 
                {% assign session_number_padded = session_order | prepend: "00" | slice: -2, 2 %}
                <li>
                  <a href="{{ '/assets/presentations/' | relative_url }}sesion_S{{ session_number_padded }}.pptx"
                    target="_blank"
                    class="resource-button resource-button--primary"> 
                    Descargar Presentación <span class="icon">↓</span>
                  </a>
                </li>
                <li>
                  <a href="{{ '/assets/activities/' | relative_url }}Actividad_S{{ session_number_padded }}.pdf"
                    target="_blank"
                    class="resource-button resource-button--success"> 
                    Descargar Actividad <span class="icon">↓</span>
                  </a>
                </li>
                
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
              
              <div class="item-actions"> 
                <a href="{{ current_session.url | relative_url }}" class="button button-secondary">Ver Sesión →</a>
              </div>
            </div>
          {% endif %}
        {% endfor %}
      </div>
    </section>
  {% endfor %}
</div>
