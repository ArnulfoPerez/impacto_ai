---
layout: default
title: Bloques del Curso
permalink: /bloques/
---

# 📚 Bloques del Curso

_Explora los diferentes bloques temáticos que componen este curso, cada uno con una perspectiva única sobre la Inteligencia Artificial y su impacto._

---

<div class="block-list">
  {% assign sorted_block_keys = site.blocks_metadata | map: "first" | sort %}
  {% for block_slug in sorted_block_keys %}
    {% assign block_data = site.blocks_metadata[block_slug] %}
    <div class="block-item">
      <h2><a href="{{ site.baseurl }}/{{ block_slug }}/">{{ block_data.icon }} {{ block_data.title }}</a></h2>
      <p>{{ block_data.description }}</p>

      <h4>Sesiones en este bloque:</h4>
      <ul>
        {% if block_slug == 'inteligencia' %}
          <li><a href="{{ site.baseurl }}/inteligencia/intro/">Sesión 1: Introducción</a></li>
          <li><a href="{{ site.baseurl }}/inteligencia/fundamentos/">Sesión 2: Fundamentos conceptuales e historia de la inteligencia artificial (IA)</a></li>
        {% elsif block_slug == 'infraestructura' %}
          <li><a href="{{ site.baseurl }}/infraestructura/modelos/">Sesión 3: Modelos, datos y entrenamiento</a></li>
          <li><a href="{{ site.baseurl }}/infraestructura/infraestructura/">Sesión 4: Infraestructura de IA</a></li>
        {% elsif block_slug == 'impacto' %}
          <li><a href="{{ site.baseurl }}/impacto/individual/">Sesión 5: Impacto individual de la IA, oportunidades y riesgos</a></li>
          <li><a href="{{ site.baseurl }}/impacto/institucional/">Sesión 6: IA en las organizaciones: Estrategias empresariales</a></li>
        {% elsif block_slug == 'percepcion' %}
          <li><a href="{{ site.baseurl }}/percepcion/sociocultural/">Sesión 7: La percepción sociocultural de la IA</a></li>
          <li><a href="{{ site.baseurl }}/percepcion/cierre/">Sesión 8: El impacto socioeconómico de la IA</a></li>
        {% else %}
          <li>No hay sesiones definidas para este bloque aún.</li>
        {% endif %}
      </ul>
    </div>
  {% endfor %}
</div>
