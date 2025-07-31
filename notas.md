---
layout: default
title: Notas del Curso
permalink: /notas/
---

<div class="list-container"> {# Consolidated: Replaced notes-list-container with list-container #}
  <header class="list-page-header"> {# Consolidated: Replaced notes-list-header with list-page-header #}
    <h1>Notas y Apuntes Adicionales</h1>
    <p class="subtitle">Aquí encontrarás recursos complementarios y apuntes detallados sobre diversos temas del curso.</p>
  </header>

  <section class="block-section"> {# This section can be used to wrap the grid if you want a card-like block for the entire list, or remove if you want grid directly #}
    {% assign sorted_notes = site.notes | sort: "title" %}

    {% if sorted_notes.size > 0 %}
      <ul class="item-grid"> {# Consolidated: Replaced notes-grid with item-grid #}
        {% for note in sorted_notes %}
          <li class="item-card"> {# Consolidated: Replaced note-card with item-card #}
            <h3 class="item-title"><a href="{{ note.url | relative_url }}">{{ note.title }}</a></h3> {# Consolidated: Replaced h3 with item-title #}
            {% if note.description %}
              <p class="item-description">{{ note.description | strip_html | truncatewords: 30 }}</p> {# Consolidated: Added item-description #}
            {% else %}
              <p class="item-description">Esta nota no tiene una descripción corta. Haz clic para leer el contenido completo.</p>
            {% endif %}
            <div class="item-actions"> {# Added wrapper for consistency #}
                <a href="{{ note.url | relative_url }}" class="button button-secondary">Leer Nota →</a>
            </div>
          </li>
        {% endfor %}
      </ul>
    {% else %}
      <p class="no-notes-message">Aún no hay notas disponibles. ¡Vuelve pronto para ver más contenido!</p>
    {% endif %}
  </section> {# Close the block-section if you used it #}
</div>
