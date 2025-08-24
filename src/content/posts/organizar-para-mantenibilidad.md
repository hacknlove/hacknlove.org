---
title: "¿Cómo organizar el código de cara a la mantenibilidad? A grandes rasgos."
published: 2025-08-01
description: "¿Cómo organizar el código? A grandes rasgos."
author: "hacknlove"
tags: ["Arquitectura", "teoría"]
draft: false
---

Este artículo va a analizar este tema desde una perspectiva teórica de brocha muy gorda, en lo que respecta a la mantenibilidad del código.

## Presentación (La realidad)

Nuestro trabajo consiste en organizar recursos para satisfacer requisitos.

Eso es todo lo que hacemos.

### Los requisitos:

Los requisitos responden a necesidades de negocio, y nos los dan los product owners.

* registrar un usuario
* publicar un producto
* hacer una búsqueda
* Añadir un producto a un carrito
* dejar un comentario

### Los Recursos

Los recursos que organizamos son principalmente de tipo tecnológico: 

* Hardware
* servidores
* Bases de datos
* servicios
* protocolos de comunicación
* Clientes
* Interfaces
* lenguajes de programación
* frameworks
* bibliotecas
* herramientas
  
pero también nosotros mismos somos parte de los recursos que tenemos que organizar:
* equipos de desarrolladores
* roles (desarrolladores, QAs, devops, etc.)
* documentación
* gestión de proyectos


## Nudo (El conflicto)

Los recursos tecnológicos nos ofrecen horizontalidades, muchas veces apiladas en capas y que son necesarias para satisfacer múltiples requisitos de negocio; mientras que los requisitos de negocio se nos presentan como verticalidades y requieren de ḿultiples capas tecnológicas.

Independientemente de los paradigmas y las arquitecturas que se utilicen, solucionar el problema primario (satisfacer los requisitos de negocio con los recursos tecnológicos) es sencillo.

El problema secundario es el que resulta más complicado, y a la postre más relevante para el éxito a largo plazo de la organización: encontrar de todas las soluciones primarias posibles, cuál ofrece la mayor calidad.

### Nuestros criterios de calidad:

Los critarios de calidad son características que desamos que tenga nuestro sistema, aunque no sean directamente necesarias para satisfacer los requisitos de negocio.

* rendimiento
* escalabilidad
* seguridad
* usabilidad que concierne a la organización del código, se
* mantenibilidad

Puede haber también criterios de calidad de negocio, que sean directamente necesarios para satisfacer los requisitos de negocio, pero en tal caso deben considerarse como requisitos de negocio.

## Desenlace (La solución)

Cualquier solución a este problema se va a situar el algún punto entre organización puramente horizontal y organización puramente vertical.

Y tanto ambas soluciones, como todos los puntos intermedios, tienen sus ventajas y sus inconvenientes.

No existe una solución práctica genérica que siempre sea la mejor, pero la experiencia nos enseña que ciertas decisiones tienen a ciertas consecuencia.

Supongamos que todas los los puntos de un extremo a otro son posibles, e idempotentes en lo que corresponde al resto de criterios de calidad.

Cuanto más horizontal sea la organización, más fácil será abordar tareas de tipo horizontal, como por ejemplo actualizar la versión de la base de datos.

Cuanto más vertical sea la organización, más fácil será abordar tareas de tipo vertical, como por ejemplo añadir la posibilidad de compartir un carrito de compras.

Mi preferencia es tener equipos muy verticales (formados por PO, QAs, diseñadores, frontend, backend, devops ) que trabajan en un código organizado de forma muy vertical (locaLity of behavior).

Y esa es mi preferencia porque tal configuración facilita las tareas de tipo vertical, que son el tipo de tareas con las que estaremos trabajando el 99% del tiempo.

## Plot twist (La sorpresa)

El problema es que ese 1% de tareas muy horizontales, como por ejemplo actualizar la versión de la base de datos, suelen ser muy grandes, muy complejas y muy críticas, por lo que mucha gente comete el error de construir organizaciones horizontales para poder abordarlas con mayor facilidad; a pesar de que eso les obligará a pagar un peaje extra en el 99% restante de las tareas.

## Conclusión (La consistencia al rescate):

Si en una organización vertical, hay suficiente consistencia horizontal, ese 1% de tareas muy horizontales se puede abordar con relativa facilidad.

Por mucho que nos preocupen las grandes tareas horizontales que antes o después tendremos que afrontar, no debemos renunciar a organizar nuestro código y nuestros equipos de forma vertical, sino que debemos dotar a nuestras organizaciones de suficiente consistencia horizontal como para las tareas horizontales puedan realizarse sin demasiado sufrimiento.


Muchas veces, se intenta lo contrario: organizaciones muy horizontales con consistencia vertical. Desde mi punto de vista, si bien no es del todo un desastre y puede tener sentido en algunos casos, por norma general, y basándome en mi experiencia, recomiendo la organización vertical con consistencia horizontal.
