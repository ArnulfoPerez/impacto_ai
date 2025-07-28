---
layout: default
title: Inicio
---

<main class="home">
    <section>
        <h1>Bienvenido al Curso: {{ site.title }}</h1>
        <p>{{ site.description }}</p>
        <p>Este curso explora en profundidad la inteligencia artificial, desde sus fundamentos técnicos hasta sus profundas implicaciones éticas y sociales.</p>
        <p>Navega a través de los diferentes módulos (Bloques) para comenzar:</p>
    </section>

    <section class="blocks-container">
        <h2>Módulos del Curso (Bloques)</h2>
        <div class="blocks-grid"> {# Un contenedor para tus bloques, puedes estilizarlo con CSS Grid/Flexbox #}
            {% assign sorted_blocks = site.blocks | sort: "order" %}
            {% for block in sorted_blocks %}
                <div class="block-card"> {# Puedes estilizar esta tarjeta en _components.scss #}
                    <h3><a href="{{ block.url | relative_url }}">{{ block.title }}</a></h3>
                    <p>{{ block.description }}</p>
                    {% if block.sessions %}
                        <h4>Sesiones en este Módulo:</h4>
                        <ul>
                            {% assign sorted_sessions_in_block = block.sessions | sort: "order" %}
                            {% for session in sorted_sessions_in_block %}
                                <li><a href="{{ session.url | relative_url }}">{{ session.title }}</a></li>
                            {% endfor %}
                        </ul>
                    {% endif %}
                </div>
            {% endfor %}
        </div>
    </section>

    {# Puedes añadir más secciones aquí, como un resumen del instructor, testimonios, etc. #}
</main>
