---
layout: default
title: Bloques del Curso
permalink: /bloques/
---
 
# 📚 Bloques del Curso

_Explora los diferentes bloques temáticos que componen este curso, cada uno con una perspectiva única sobre la Inteligencia Artificial y su impacto._

---

<div class="block-list">
    {% assign sorted_block_keys = site.blocks_metadata | map: "first" | sort %} {# Obtiene las claves y las ordena alfabéticamente #}
    {% for block_slug in sorted_block_keys %}
        {% assign block_data = site.blocks_metadata[block_slug] %}
        <div class="block-item">
            <h2><a href="{{ site.baseurl }}/{{ block_slug }}/">{{ block_data.icon }} {{ block_data.title }}</a></h2>
            <p>{{ block_data.description }}</p>
            {% assign sessions_in_block = site.sessions | where: "block", block_slug | sort: "order" %}
            {% if sessions_in_block.size > 0 %}
                <h4>Sesiones en este bloque:</h4>
                <ul>
                    {% for session in sessions_in_block %}
                        <li><a href="{{ session.url | relative_url }}">Sesión {{ session.order }}: {{ session.title }}</a></li>
                    {% endfor %}
                </ul>
            {% endif %}
        </div>
    {% endfor %}
</div>
