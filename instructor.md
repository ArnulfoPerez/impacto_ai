---
layout: default
title: Sobre el Instructor
permalink: /instructor/ # Asegura que la URL sea /instructor/
---

<section class="instructor-page-intro">
    <h1>{{ page.title }}</h1>
    <p class="lead">Conoce al experto que te guiará a través de este fascinante curso.</p>
</section>

<section class="instructor-details">
    {# Incluimos la tarjeta del instructor que ya hemos definido #}
    {% include instructor_card.html %}
 
    <div class="instructor-bio">
        <p>Desde siempre me ha fascinado la mente humana; entender cómo funciona y como se pudiera emular. Mi niñez coincidió con el desarrollo de la Cibernética por Norbert Wiener y el mexicano Arturo Rosenblueth. Digamos la época romántica de la Inteligencia Artificial. La Cibernética estudia sistemas que mantienen un estado homeostático, persiguen objetivos y se adaptan a su entorno. En los años 60, Marvin Minsky-junto con Seymour Papert jugó un papel crucial en definir los límites y posibilidades de la inteligencia artificial temprana, especialmente a través de su análisis del perceptrón. El perceptrón, propuesto inicialmente por Frank Rosenblatt, era un modelo de red neuronal simple que prometía emular ciertas capacidades cognitivas humanas, como el reconocimiento visual. En ese momento, las expectativas eran altísimas: se pensaba que las máquinas podrían aprender a ver, razonar y actuar como humanos en cuestión de décadas. Esta visión ha guiado mi formación, donde he buscado entender como intervenir en sistemas complejos tecnológicos, sociales y humanos desde una perspectiva estructurada y sistémica.</p>

        <p>Me formé como fisico en la Universidad Autónoma de Nuevo León, y luego realicé una Maestría y Doctorado en Ingeniería Eléctrica y Computacional en la Universidad de Tennessee. A lo largo de mi carrera he estado involucrado con los métodos cuantitativos de toma de decisiones, el análisis de datos, el aprendizaje automático y la teoría de sistemas. He impartido cursos en múltiples instituciones, abordando temas como inteligencia artificial, lógica computacional, optimización y planeación estratégica. En el ámbito profesional, he sido consultor, profesor investigador y desarrollador de modelos en contextos que van desde la industria manufacturera hasta la planificación financiera. He colaborado en proyectos del Centro de Inteligencia Artificial del ITESM, y he implementado soluciones tecnológicas con base en una comprensión de cómo interactúan las personas, la tecnología y los procesos.</p>
    </div>

    <div class="instructor-credentials">
        <h2>Credenciales Académicas</h2>
        <ul>
            <li>**Ph. D.** Electrical and Computer Engineering 1986 - 1989, **THE UNIVERSITY OF TENNESSEE, KNOXVILLE**, Disertación: *Parallel Segmentation of Range Images on a Hypercube-connected Distributed Computer*.</li>
            <li>**M.S.** Electrical and Computer Engineering 1980-1986, **THE UNIVERSITY OF TENNESSEE, KNOXVILLE**, Tesis: *Mask Decompositions for Digital Image Processing*.</li>
            <li>**Licenciatura en Física** 1976-1979, **UNIVERSIDAD AUTÓNOMA DE NUEVO LEÓN**, Tesis: *Análisis Teórico experimental del comportamiento temporal de potenciales transmembrana de un axón*.</li>
        </ul>
    </div>
</section>
