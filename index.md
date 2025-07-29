---
layout: default
title: Inicio
---

<main class="home">
    <section class="course-intro">
        <h1>Bienvenido al Curso: {{ site.title }}</h1>
        <p>{{ site.description }}</p>
        <p>Este curso explora en profundidad la inteligencia artificial, desde sus fundamentos técnicos hasta sus profundas implicaciones éticas y sociales.</p>

        <h2>Objetivos Generales del Curso</h2>
        <ul class="course-objectives">
            {% for objective in site.course.objectives %}
                <li>{{ objective }}</li>
            {% endfor %}
        </ul>
        <p>Navega a través de los diferentes módulos (Bloques) para comenzar:</p>
    </section>

    <section class="blocks-container">
        <h2>Módulos del Curso</h2>
        <div class="blocks-grid">
            {% assign sorted_blocks = site.blocks | sort: "order" %}
            {% for block in sorted_blocks %}
                {% assign block_slug = block.slug %}
                {% assign block_meta = site.blocks_metadata[block_slug] %}

                <div class="block-card">
                    <div class="block-header">
                        {% if block_meta.icon %}
                            <span class="block-icon">{{ block_meta.icon }}</span>
                        {% endif %}
                        <h3><a href="{{ block.url | relative_url }}">{{ block_meta.title | default: block.title }}</a></h3>
                    </div>
                    <p class="block-description">{{ block_meta.description | default: block.description }}</p>

                    {% if block.sessions %}
                        <h4>Sesiones:</h4>
                        <ul class="session-list">
                            {% assign sorted_sessions_in_block = block.sessions | sort: "order" %}
                            {% for session in sorted_sessions_in_block %}
                                {% assign session_slug = session.slug %}
                                {% assign session_meta = site.session_metadata[block_slug][session_slug] %}
                                <li class="session-item">
                                    <a href="{{ session.url | relative_url }}">{{ session_meta.title | default: session.title }}</a>
                                    {% if session_meta.description %}
                                        <p class="session-description">{{ session_meta.description }}</p>
                                    {% endif %}
                                    {% if session_meta.obj %}
                                        <ul class="session-objectives">
                                            {% for obj in session_meta.obj %}
                                                <li>{{ obj }}</li>
                                            {% endfor %}
                                        </ul>
                                    {% endif %}
                                </li>
                            {% endfor %}
                        </ul>
                    {% endif %}
                </div>
            {% endfor %}
        </div>
    </section>

    <section class="instructor-section">
        <h2>Sobre el Instructor</h2>
        {% include instructor_card.html %}
    </section>
    {# Puedes añadir más secciones aquí, como un resumen del instructor, testimonios, etc. #}
</main>
