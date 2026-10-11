# 🌐 ctOS // Global Official Sec-Grid

> **Terminal Táctica de Geoposicionamiento, Navegación y Monitoreo de Red**  
> *Una experiencia cartográfica inmersiva basada en la estética ctOS de Watch Dogs.*

![ctOS Banner](https://img.shields.io/badge/ctOS-Grid_Online-00f3ff?style=for-the-badge&logo=leaflet)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Leaflet](https://img.shields.io/badge/Leaflet-199900?style=for-the-badge&logo=leaflet&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-00f3ff?style=for-the-badge)

---

## 📄 Tabla de Contenidos

1. [Visión General](#-visión-general)
2. [Características Destacadas](#-características-destacadas)
3. [Arquitectura y Estructura del Código](#-arquitectura-y-estructura-del-código)
4. [Módulos e Interfaz (HUD)](#-módulos-e-interfaz-hud)
5. [Instalación y Despliegue](#-instalación-y-despliegue)
    * [Ejecución Local](#1-ejecución-local)
    * [Despliegue con GitHub Pages](#2-despliegue-en-github-pages)
6. [Soporte PWA y Offline Storage](#-soporte-pwa-y-offline-storage)
7. [Configuración de `manifest.json`](#-configuración-de-manifestjson)
8. [Personalización y Extensión](#-personalización-y-extensión)
9. [Contribución](#-contribución)
10. [Licencia](#-licencia)

---

## 👁️ Visión General

**ctOS // Global Official Sec-Grid** es una aplicación web interactiva de mapas que transforma la cartografía tradicional en una terminal de inteligencia y monitoreo urbano. Inspirada en la interfaz visual de la saga de videojuegos *Watch Dogs*, la aplicación ofrece una experiencia táctica sobre navegadores de escritorio y dispositivos móviles.

Construida íntegramente en **Vanilla JavaScript**, la aplicación combina **Leaflet.js**, **OpenStreetMap**, la API de **OSRM** para el trazado de rutas vehiculares, y tecnologías de almacenamiento avanzado como la **Cache API** para garantizar la disponibilidad de mapas incluso sin cobertura de internet.

---

## ⚡ Características Destacadas

### 🎨 1. Estética y HUD Ciberpunk
*   **Filtro Cartográfico Exclusivo:** Inversión de tonos, ajuste de contraste, saturación y matriz de color (`hue-rotate`) sobre las capas de mapas estándar para simular una visión nocturna/monocromática de red.
*   **Diseño Adaptable (Mobile-First):** Ajuste dinamizado para dispositivos táctiles, celulares y tablets con protección de áreas seguras (safe areas).

### 🔍 2. Geocodificación y Búsqueda Inteligente
*   **Autocompletado en Tiempo Real:** Búsqueda dinámica con *debounce* (retardo de petición) mediante la API de **Nominatim**.
*   **Búsqueda Acotada por Visor:** Priorización de resultados basados en la región del mapa actualmente visible (`viewbox`).
*   **Reverse Geocoding:** Decodificación instantánea de direcciones y nombres de edificios/comercios al hacer clic en cualquier punto de la matriz cartográfica.

### 🧭 3. Navegación GPS en Vivo
*   **Cálculo de Rutas Automático:** Conexión con **OSRM** para el cálculo óptimo de distancias vehiculares.
*   **Indicaciones Turn-by-Turn:** Banner superior con detección de maniobras (*girar a la derecha, izquierda, rotondas, etc.*) e iconos direccionales.
*   **Panel de Métricas Activas:** Monitoreo dinámico del tiempo estimado de llegada (ETA), duración restante y kilómetros faltantes.
*   **Rastreo por Marcador GPS:** Marcador fluido del operador mediante `navigator.geolocation.watchPosition`.

### 💾 4. Almacenamiento y Modo Sin Conexión
*   **Descarga de Teselas Reales:** Módulo especializado para iterar e interpolar coordinadas cartográficas (Tile X, Y, Z) y almacenarlas en la **Cache API** del navegador.
*   **Base de Datos de Objetivos:** Guardado persistente de lugares favoritos utilizando `localStorage`.

---

## 🏗️ Arquitectura y Estructura del Código

El proyecto ha sido diseñado para mantenerse ágil, sin necesidad de instaladores de paquetes, entornos de Node.js ni compiladores. Todo el núcleo del sistema funciona de manera nativa en el navegador.

```text
ctOS-sec-grid/
│
├── index.html           # Aplicación principal (HTML5 + CSS3 + JS Engine)
├── manifest.json        # Configuración para instalación PWA (Web App Manifest)
├── icon-192.png         # Icono para la pantalla de inicio (192x192)
├── icon-512.png         # Icono de alta resolución (512x512)
└── README.md            # Documentación oficial del repositorio
