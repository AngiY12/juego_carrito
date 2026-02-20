# 🏎️ Simulador de Carrera 3D con OpenGL y Python

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat&logo=python)
![OpenGL](https://img.shields.io/badge/OpenGL-PyOpenGL-5586A4?style=flat&logo=opengl)
![Status](https://img.shields.io/badge/Estado-Completado-success)

Un simulador de conducción en 3D desarrollado completamente en Python utilizando **OpenGL (GLUT)**. Este proyecto renderiza un entorno tridimensional con generación de escenarios, texturizado de objetos, iluminación dinámica y físicas básicas de conducción.

## ✨ Características Principales

* **Modelo 3D y Controles:** Vehículo interactivo compuesto por primitivas de OpenGL con controles de aceleración, frenado y rotación.
* **Curvas de Bézier:** Generación paramétrica de la carretera utilizando curvas de Bézier cúbicas para un trazado suave.
* **Ciclo Día/Noche Dinámico:** Transición de luz y color del cielo automatizada y basada en la posición del vehículo en el mapa (incluye luz solar y simulación de luz lunar).
* **Sombras en Tiempo Real:** Sistema de proyección de sombras planas sin usar shaders complejos, calculando la intersección con el suelo según la posición de la fuente de luz.
* **Cámaras Alternables:** Intercambio en tiempo real entre vista de perspectiva (cámara en tercera persona) y vista ortogonal (cámara cenital/isométrica).
* **Texturizado:** Mapeo de texturas 2D (con `Pillow`) para la carretera, las montañas y el césped.
* **Físicas de Entorno:** Implementación de fricción, inercia y un sistema de "penalización" de velocidad si el auto sale de la carretera hacia el césped.

## 🛠️ Requisitos Previos

Para ejecutar este proyecto, asegúrate de tener instalado Python en tu sistema, junto con las siguientes librerías:
```bash
pip install PyOpenGL PyOpenGL_accelerate
pip install Pillow
```
## 📂 Recursos Necesarios (Assets)
El script busca los siguientes archivos de imagen en el directorio raíz para aplicar las texturas. Si no los encuentra, el programa no se detendrá y aplicará colores sólidos por defecto para evitar errores:

* asfalto.jpg (Textura para la carretera)

* hierba.jpg (Textura para el suelo/entorno)

* montana.jpg (Textura para las montañas del fondo)

## 🏗️ Estructura del Código
El proyecto está diseñado bajo el paradigma de Programación Orientada a Objetos (POO), dividiendo las responsabilidades de la siguiente manera:

* Textura: Manejo y carga de imágenes en memoria usando la librería PIL.

* Objeto3D: Clase base abstracta que maneja las matrices de traslación, rotación y escalado (glPushMatrix, glPopMatrix).

* Subclases (Auto, Casa, Montana, Carretera, Arbol, Suelo): Cada una hereda de Objeto3D y define su propio método _dibujar() utilizando las primitivas gráficas de GLUT.

* Escena: Orquestador principal que maneja el loop de renderizado general, las cámaras, la iluminación y la detección de salidas de pista.
