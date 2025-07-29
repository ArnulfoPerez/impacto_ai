---
layout: default
title: Inicio
permalink: /
---

# {{ site.title }}

{{ site.description }}

{% assign instructor = site.instructor %}

## 👨‍🏫 Instructor
**{{ instructor.name }}**  
{{ instructor.position }} en {{ instructor.institution }}  
📧 [{{ instructor.email }}](mailto:{{ instructor.email }})  
🔗 [Perfil de LinkedIn]({{ instructor.linkedin }})

## 🎯 Objetivos del Curso
<ul class="objectives">
  {% for objective in site.course.objectives %}
    <li>{{ objective }}</li>
  {% endfor %}
</ul>

## 📚 Bloques Temáticos

<div class="blocks-container">
  {% assign blocks = site.blocks_metadata | sort: "order" %}
  {% for block in blocks %}
    <div class="block-card">
      <h3>{{ block[1].icon }} {{ block[1].title }}</h3>
      <p>{{ block[1].description }}</p>
      <div class="sessions-list">
        <h4>Sesiones:</h4>
        <ul>
          {% assign sessions = site.session_metadata[block[0]] %}
          {% for session in sessions %}
            <li>
              <strong>{{ session[1].title }}</strong>:
              {{ session[1].description }}
            </li>
          {% endfor %}
        </ul>
      </div>
    </div>
  {% endfor %}
</div>

## 🔗 Navegación Rápida
<ul class="quick-links">
  {% for item in site.navigation %}
    <li><a href="{{ item.url | relative_url }}">{{ item.title }}</a></li>
  {% endfor %}
</ul>

<style>
  .blocks-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
    margin: 30px 0;
  }
  
  .block-card {
    background: #f8f9fa;
    border-radius: 8px;
    padding: 20px;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  }
  
  .block-card h3 {
    margin-top: 0;
    color: #2c3e50;
  }
  
  .sessions-list {
    margin-top: 15px;
    padding-top: 15px;
    border-top: 1px solid #eee;
  }
  
  .objectives, .quick-links {
    padding-left: 20px;
  }
  
  .quick-links {
    display: flex;
    gap: 15px;
    list-style: none;
    padding: 0;
  }
</style>

{% seo %}
