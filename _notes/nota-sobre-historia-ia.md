---
layout: note # (or remove if using defaults in _config.yml)
title: Breve Historia de los Algoritmos de IA
id: nota-sobre-historia-ia
date: 2025-07-29
author: Dr. Arnulfo Pérez
tags: ["historia", "algoritmos", "fundamentos"]
introduction: |
  La Inteligencia Artificial ha evolucionado a través de décadas de investigación y desarrollo. Comprender su trayectoria algorítmica es clave para apreciar el estado actual de la IA.
main_points: |
  * **Primeros Pasos (1950s-1970s):** Surgimiento del Perceptrón y los programas de IA basados en reglas. Limitaciones computacionales y el "invierno de la IA".
  * **Resurgimiento y Redes Neuronales (1980s-2000s):** Desarrollo del algoritmo Backpropagation, abriendo nuevas posibilidades para el aprendizaje profundo.
  * **La Era del Deep Learning (2010s-Presente):** Avances en hardware (GPUs) y la disponibilidad de grandes datasets impulsan el éxito de las redes neuronales profundas en reconocimiento de imágenes, voz y procesamiento de lenguaje natural.
conclusion: |
  La historia de la IA es un testimonio de persistencia y avance iterativo. Cada era ha construido sobre la anterior, llevándonos a la poderosa IA que conocemos hoy, con un potencial aún inmenso por explorar.
references: |
  * Russell, Stuart J., and Peter Norvig. *Artificial Intelligence: A Modern Approach*. Pearson Education Limited, 2010.
  * Goodfellow, Ian, Yoshua Bengio, and Aaron Courville. *Deep Learning*. MIT Press, 2016.
---



---

## 🔷 Definición clave

<div class="bloque definicion">
La inteligencia artificial (IA) es la capacidad de una máquina para imitar funciones cognitivas humanas como el aprendizaje, la percepción y la toma de decisiones.
</div>

---

## 🧮 Ejemplo con MathJax

La ecuación de probabilidad condicional en modelos de lenguaje es:

$$ P(w_t \mid w_1, w_2, \ldots, w_{t-1}) $$

Donde $w_t$ es el token actual, y $w_{t-1}$ los anteriores en la secuencia.

## Fórmulas matemáticas en línea

La famosa ecuación de Einstein es $E = mc^2$.

El teorema de Pitágoras establece que en un triángulo rectángulo: 
\\( a^2 + b^2 = c^2 \\).

La derivada de \\( x^n \\) es \\( nx^{n-1} \\).

---

## 🐍 Bloque de código en Python

```python
import random

def generar_token(contexto):
    vocabulario = ["IA", "ética", "modelo", "alineación"]
    return random.choice(vocabulario)

print(generar_token("La IA puede"))
```

---

## 📊 Diagrama Mermaid

<div class="mermaid">
flowchart TD
  Inicio["Inicio del modelo"] --> Token1["Token 1"]
  Token1 --> Token2["Token 2"]
  Token2 --> Decision["Decisión final"]
  Decision --> Resultado["Resultado generado"]
</div>
# Diagrama de ejemplo con Mermaid

Aquí hay un diagrama de flujo generado con Mermaid:

<div class="mermaid">
graph TD;
    A[Inicio] --> B{Es un día soleado?};
    B -->|Sí| C[Ve a la playa];
    B -->|No| D[Quedate en casa];
    C --> E[Termina];
    D --> E;
</div>

Y aquí un diagrama de secuencia:

<div class="mermaid">
sequenceDiagram
    participant Usuario
    participant Sitio
    Usuario->>Sitio: Carga la página
    Sitio-->>Usuario: Muestra contenido
    Usuario->>Sitio: Hace clic en botón
    Sitio-->>Usuario: Muestra modal
</div>
---


# Demostración de Componentes Estilizados

## 🧩 Definición Temática

<div class="definicion">
**Término:** Canonical Structure  
**Definición:** Organización de archivos SCSS según las mejores prácticas de Jekyll, separando variables, mixins y componentes en archivos parciales.
</div>

---

## ⚠️ Advertencia Importante

<div class="advertencia">
**¡Atención!**  
No modificar directamente los archivos CSS generados. Siempre editar los archivos SCSS en `_sass/` y dejar que Jekyll los compile.
</div>

---

## 💡 Ejemplo Práctico

<div class="ejemplo">
**Caso de Uso:** Este contenido aparecerá con fondo rojo claro.
</div>

---

## 📌 Tarea sugerida

- Escribe un prompt que provoque una respuesta alucinada por parte de un modelo generativo.
- Genera un diagrama Mermaid que represente cómo una IA decide un output basado en contexto limitado.
- Identifica el token al que se le asignaría mayor probabilidad en una frase como "La ética de la IA requiere..."
