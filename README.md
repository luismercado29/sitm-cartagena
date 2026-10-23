<div align="center">

# 🚌 SITM Cartagena · Despacho de buses

**Centro de despacho para un sistema de transporte masivo**, con mapa en vivo de la flota y un portal para que el pasajero sepa cuándo llega su bus.

[![Demo](https://img.shields.io/badge/Ver%20demo-sistematizacion--sitm.vercel.app-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://sistematizacion-sitm.vercel.app)
[![Portafolio](https://img.shields.io/badge/Detalle%20en%20el%20portafolio-E34F26?style=for-the-badge&logo=astro&logoColor=white)](https://luis-mercado-portfolio.vercel.app/proyectos/sistematizacion-sitm)
![Estado](https://img.shields.io/badge/Estado-En%20producci%C3%B3n-2EA44F?style=for-the-badge)

<img src="docs/portada.jpg" alt="Portada de SITM Cartagena" width="100%" />

</div>

> 🔒 **Repositorio de presentación.** El código fuente es privado. Aquí encontrarás la descripción, la arquitectura y capturas del sistema. Si quieres conocer el código para un proceso de selección, [escríbeme](mailto:luisda3329@hotmail.com).

---

## 📌 Qué es

Aplicación que digitaliza el despacho de buses de un sistema integrado de transporte masivo en Cartagena y elimina el uso de papel en la operación:

- **Los despachadores** programan y despachan buses por ruta, controlan la flota y los conductores y siguen cada recorrido en un mapa en vivo.
- **Los pasajeros** consultan desde el celular qué buses vienen a su estación y en cuántos minutos, sin instalar nada.

Las 24 rutas están trazadas sobre las vías reales, y un modo demostración simula los buses en movimiento con tiempos de recorrido realistas.

## ✨ Funcionalidades

- 📊 **Tablero de operación:** buses en ruta, puntualidad, frecuencia por ruta y conductores con licencia por vencer.
- 🚦 **Despacho** con validación de bus y conductor disponibles, inicio, novedades y cierre del recorrido.
- 🗺️ **Mapa en vivo** con la flota moviéndose sobre 24 rutas y 36 estaciones trazadas con datos de OpenStreetMap.
- 📱 **Portal del pasajero** con llegadas estimadas por estación, actualizado cada pocos segundos.
- 🚌 **Gestión de flota y conductores;** registro de despachos con filtros y exportación CSV.
- 🔐 Roles de supervisión y despacho, política CSP estricta, límite de intentos de inicio de sesión y base de datos en Neon.

## 🖼️ Capturas

| | |
|---|---|
| <img src="docs/03-tablero.jpg" alt="Tablero" /> <br/> **Tablero de operación** del despacho | <img src="docs/04-mapa-operativo.jpg" alt="Mapa operativo" /> <br/> **Mapa en vivo** de la flota por ruta |
| <img src="docs/05-despachos.jpg" alt="Despachos" /> <br/> **Registro de despachos** con filtros | <img src="docs/06-flota.jpg" alt="Flota" /> <br/> **Estado de la flota** |
| <img src="docs/01-inicio-publico.jpg" alt="Portal del pasajero" /> <br/> **Portal del pasajero** | <img src="docs/02-mapa-publico.jpg" alt="Mapa público" /> <br/> **Mapa público** en vivo |

## 🏗️ Arquitectura

```mermaid
flowchart LR
    PAS[Pasajero] --> PUB
    DES[Despachador / Supervisor] --> OPS
    subgraph App["Django 5"]
        PUB[Portal público<br/>llegadas por estación]
        OPS[Centro de despacho<br/>tablero · despachos · flota]
        RED[Red de rutas<br/>24 rutas · 36 estaciones]
        SIM[Simulador de recorridos]
    end
    DB[(PostgreSQL · Neon)]
    OSM[OpenStreetMap<br/>Leaflet · Mapbox]

    PUB --> DB
    OPS --> DB
    RED --> DB
    SIM --> DB
    RED -. trazado de vías .-> OSM
    PUB --> OSM
    OPS --> OSM
```

## 🛠️ Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Neon](https://img.shields.io/badge/Neon-00E599?style=for-the-badge&logo=neon&logoColor=black)
![Leaflet](https://img.shields.io/badge/Leaflet-199900?style=for-the-badge&logo=leaflet&logoColor=white)
![Mapbox](https://img.shields.io/badge/Mapbox-000000?style=for-the-badge&logo=mapbox&logoColor=white)
![OpenStreetMap](https://img.shields.io/badge/OpenStreetMap-7EBC6F?style=for-the-badge&logo=openstreetmap&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)

---

<div align="center">

Hecho por **[Luis Mercado](https://github.com/luismercado29)** · Desarrollo full-stack · Proyecto académico rediseñado en 2026

© 2026 Luis Mercado. Todos los derechos reservados.

</div>
