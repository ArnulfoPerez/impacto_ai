---
layout: default
title: Home
---

# ¡Bienvenido al Curso de Impacto Social de la Inteligencia Artificial!

Este es el sitio web de nuestro curso, donde podrás encontrar toda la información sobre los bloques, sesiones, actividades y presentaciones.

---

<h2 style="text-align: center;">Nuestros Bloques Temáticos</h2>
<p style="text-align: center;">_Haz clic en un bloque para ver sus detalles y sesiones._</p>

<div class="block-overview-list">
  {% comment %} Convert blocks_metadata hash to an array of values and sort by 'order' {% endcomment %}
  {% assign ordered_blocks = site.blocks_metadata | values | sort: "order" %} {# <-- FIX HERE! #}

  {% for block_data in ordered_blocks %} {# <-- Iterate directly over block_data now #}
    {% assign block_slug = block_data.slug | default: block_data.title | slugify %} {# Fallback if slug isn't explicitly in metadata #}

    <div class="block-overview-item">
      <h3><a href="{{ site.baseurl }}/{{ block_slug }}/">{{ block_data.icon }} {{ block_data.title }}</a></h3>
      <p>{{ block_data.description }}</p>

      <h4>Sesiones:</h4>
      <ul>
        {% comment %} Find sessions belonging to this block and sort them by 'order' {% endcomment %}
        {% assign sessions_in_block = site.sessions | where: "block", block_slug | sort: "order" %}
        {% if sessions_in_block.size > 0 %}
          {% for session in sessions_in_block %}
            <li><a href="{{ session.url | relative_url }}">Sesión {{ session.order }}: {{ session.title }}</a></li>
          {% endfor %}
        {% else %}
          <li>No hay sesiones definidas para este bloque aún.</li>
        {% endif %}
      </ul>
    </div>
  {% endfor %}
</div>

---

<p style="text-align: center;">También puedes visitar las páginas de <a href="{{ site.baseurl }}/actividades/">Actividades</a> y <a href="{{ site.baseurl }}/presentaciones/">Presentaciones</a>.</p>
