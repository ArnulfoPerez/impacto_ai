---
layout: default
title: Notas del Curso
permalink: /notas/
---

<div class="list-container"> 
  <header class="list-page-header"> 
    <h1>Notas y Apuntes Adicionales</h1>
    <p class="subtitle">Aquí encontrarás recursos complementarios y apuntes detallados sobre diversos temas del curso.</p>
  </header>

  <section class="block-section">
    {% assign sorted_notes = site.notes | sort: "title" %}

    {% if sorted_notes.size > 0 %}
      <ul class="item-grid"> 
        {% for note in sorted_notes %}
          <li class="item-card"> 
            <h3 class="item-title"><a href="{{ note.url | relative_url }}">{{ note.title }}</a></h3> 
            {% if note.description %}
              <p class="item-description">{{ note.description | strip_html | truncatewords: 30 }}</p> 
            {% else %}
              <p class="item-description">Esta nota no tiene una descripción corta. Haz clic para leer el contenido completo.</p>
            {% endif %}
            <div class="item-actions"> 
                <a href="{{ note.url | relative_url }}" class="button button-secondary">Leer Nota →</a>
            </div>
          </li>
        {% endfor %}
      </ul>
    {% else %}
      <p class="no-notes-message">Aún no hay notas disponibles. ¡Vuelve pronto para ver más contenido!</p>
    {% endif %}
  </section> 
</div>
