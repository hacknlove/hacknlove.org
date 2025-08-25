---
title: "¿Cómo organizar el código para la mantenibilidad? A grandes rasgos."
published: 2025-08-01
description: "Reflexión teórica sobre cómo organizar el código con la mantenibilidad en mente."
author: "hacknlove"
tags: ["Arquitectura", "Teoría"]
draft: false
---

Este artículo aborda la organización del código desde una perspectiva amplia y teórica, centrándonos en la **mantenibilidad** como criterio de calidad.

## Presentación (La realidad)

En esencia, nuestro trabajo consiste en **organizar recursos para satisfacer requisitos**.  
Nada más, pero tampoco nada menos.

### Los requisitos
Los requisitos responden a necesidades de negocio y llegan desde los *product owners*. Ejemplos típicos:

* Registrar un usuario  
* Publicar un producto  
* Realizar una búsqueda  
* Añadir un producto al carrito  
* Dejar un comentario  

### Los recursos
Para cubrir esos requisitos disponemos de recursos de distinta naturaleza.

**Tecnológicos:**
* Hardware  
* Servidores  
* Bases de datos  
* Servicios  
* Protocolos de comunicación  
* Clientes  
* Interfaces  
* Lenguajes de programación  
* Frameworks, librerías y herramientas  

**Humanos y organizativos:**
* Equipos de desarrollo  
* Roles (desarrolladores, QAs, DevOps, etc.)  
* Documentación  
* Gestión de proyectos  

## Nudo (El conflicto)

Los recursos tecnológicos pueden imaginarse como **capas horizontales** que sirven a múltiples requisitos.  
Los requisitos de negocio, en cambio, se nos presentan como **verticalidades** que atraviesan varias capas a la vez.

El problema primario —satisfacer un requisito con los recursos disponibles— suele ser relativamente sencillo.  
El verdadero reto está en el **problema secundario**: elegir, entre todas las soluciones posibles, la que mejor equilibre calidad y sostenibilidad a largo plazo.

### Criterios de calidad
Son propiedades deseables del sistema, aunque no respondan directamente a un requisito de negocio:

* Rendimiento  
* Escalabilidad  
* Seguridad  
* Usabilidad
* Velocidad de desarrollo
* **Mantenibilidad**  

Cuando un criterio de calidad es imprescindible para satisfacer el negocio (ej. disponibilidad 24/7 en un e-commerce global), deja de ser “extra” y pasa a ser un requisito de negocio en sí mismo.

## Desenlace (La solución)

Toda organización del código se sitúa en algún punto entre dos extremos:

* **Horizontalidad pura**: optimiza las tareas horizontales (ej. casmbiar el motor de una base de datos).  
* **Verticalidad pura**: optimiza las tareas verticales (ej. añadir la opción de compartir un carrito).  

No existe una receta universal: cada decisión implica ventajas e inconvenientes.

En mi experiencia, la apuesta más efectiva es una **organización vertical del código** (*locality of behavior*), con **equipos multifuncionales** (PO, QA, diseño, frontend, backend, DevOps).  
¿Por qué? Porque la inmensa mayoría de las tareas (el famoso 99%) son verticales, y es ahí donde más conviene optimizar.

## Plot twist (La sorpresa)

Ese 1% de tareas horizontales —como migrar una base de datos o actualizar un framework crítico— son desproporcionadamente **grandes, complejas y críticas**.  
Este hecho suele llevar a muchas organizaciones a adoptar estructuras excesivamente horizontales, pagando después un peaje innecesario en el 99% de tareas habituales.



## Conclusión (La consistencia al rescate)

La clave está en una **organización vertical con consciencia horizontal**.
Una organización vertical puede manejar sin grandes dramas ese 1% de tareas horizontales si se asegura suficiente **consistencia horizontal**: estándares claros, convenciones compartidas y buenas prácticas transversales.

Por el contrario, aunque una organización horizontal con consistencia vertical es posible y en ciertos contextos puede tener sentido, en general acaba generando más fricción que beneficios.

La superioridad de la organización vertical se aprecia con claridad en los **casos extremos**:

* **Extremo vertical:** las capas horizontales de cada proyecto son completamente independientes entre sí, lo que reduce de forma natural el tamaño de ese 1% de tareas horizontales (*divide y vencerás*). Incluso en este escenario recomiendo mantener consistencia horizontal, salvo que exista una razón muy clara para no hacerlo.

* **Extremo horizontal:** no aporta ninguna ventaja en las tareas verticales —que son la inmensa mayoría— y, en cambio, multiplica los inconvenientes.


**Mi recomendación, basada en la experiencia:**  
👉 Optar por una **organización vertical** del código y de los equipos, reforzada con la **consistencia horizontal** necesaria para no sufrir en las tareas transversales.
