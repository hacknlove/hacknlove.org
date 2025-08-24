---
title: " Evitar el Próximo Desastre al Estilo Microservicios: DDD"
published: 2025-08-24
description: "Aplica DDD solo donde la complejidad del negocio lo haga necesario — y únicamente aquellas partes de DDD que realmente aporten valor a ese proyecto concreto."
author: "hacknlove"
tags: ["Arquitectura", "DDD"]
draft: false
---

## TL;DR — Resumen Ejecutivo

**Aplica DDD solo donde la complejidad del negocio lo haga necesario; y únicamente aquellas partes de DDD que realmente aporten valor a ese proyecto concreto.** 

## 1. ¿Cuándo usar DDD? La Respuesta Equivocada: 

> *“Siempre que tengas un proyecto complejo.”* 💩


Mucha gente cree que DDD es un buen enfoque para todo proyecto complejo.

Tomemos como ejemplo los proyectos open source más famosos y complejos:

* **Sistemas operativos & kernels**: Linux Kernel, Android (AOSP)
* **Servidores web & proxies**: Apache HTTP Server, Nginx, Traefik
* **Bases de datos**: PostgreSQL, MySQL, MongoDB, Redis
* **Contenedores & orquestación**: Docker, Kubernetes
* **Navegadores & entornos de escritorio**: Firefox, Chromium, GNOME, KDE
* **Editores & IDEs**: VS Code, Eclipse, IntelliJ Community, Volt (nuevo)
* **Gráficos & multimedia**: GIMP, Inkscape, Krita, Blender, Audacity, FFmpeg
* **Productividad**: LibreOffice
* **CMS & aplicaciones web**: WordPress, Drupal, Joomla
* **Seguridad & criptografía**: OpenSSL
* **Frameworks de IA/ML**: TensorFlow, PyTorch
* **Lenguajes & compiladores**: Node.js, TypeScript, Babel, Python, PHP

✅ Todos ellos abordan problemas muy complejos, y lo hacen de una forma muy exitosa.

❌ Ninguno de ellos implementa DDD.

❌ En cambio, utilizan aquellos patrones y paradigmas que mejor se adaptan a sus características concretas y que mejor solucionan sus necesidades específicas.

Si DDD fuese realmente el mejor enfoque para cualquier sistema complejo, sería esperable que al menos uno de estos proyectos lo hubiera adoptado ya. Ninguno lo ha hecho aún, y seguramente no lo harán nunca.

---

## 2. Dos Tipos de Complejidad

### Complejidad de negocio

Contratos, facturación, permisos, regulación, reglas en constante cambio.
*Ejemplos: sistemas ERP, banca, salud, plataformas de contenidos.*

En estas áreas, **DDD aporta valor**: ayuda a modelar invariantes y mantener la consistencia cuando las reglas de negocio cambian con frecuencia.

> *“DDD isn’t first and foremost about technology. In its most central principles, DDD is about discussion, listening, understanding, discovery, and business value.”*
> ([Goodreads – Vaughn Vernon quotes](https://www.goodreads.com/author/quotes/6444097.Vaughn_Vernon?utm_source=chatgpt.com))

DDD está pensado para traducir el negocio en software, no para resolver desafíos puramente técnicos.

### Complejidad de infraestructura

Rendimiento, concurrencia, redes, sistemas distribuidos, fiabilidad, tolerancia a fallos.
*Ejemplos: Linux Kernel, Kubernetes, FFmpeg, Nginx.*

Aquí, **DDD no aporta valor**. La complejidad radica en cuestiones técnicas, no en reglas de negocio.

Como dice Martin Fowler:

> *“DDD provides little advantage for problems that are algorithmically complex but have little domain complexity.”*
> ([martinfowler.com](https://martinfowler.com/bliki/DomainDrivenDesign.html?utm_source=chatgpt.com))

Y la guía oficial de microservicios de .NET de Microsoft apunta lo mismo:

> *“DDD approaches should be applied only if you are implementing complex microservices with significant business rules. Simpler responsibilities… can be managed with simpler approaches.”*
> ([Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/ddd-oriented-microservice?utm_source=chatgpt.com))


### Por qué usar DDD es perjudicial en módulos cuya complejidad es técnica

* **Carga de mantenimiento** → hay que ocuparse no solo de resolver el problema técnico, sino de ajustar el código a un conjunto de patrones y abstracciones que no tienen nada que ver con el problema.
* **Sobre-abstracción** → capas artificiales que no se ajustan al problema, que hacen el código más difícil de seguir
* **bajo rendimiento** → indirecciones y manejo de eventos innecesarios en rutas críticas.
* **baja velocidad de desarrollo** → más artefactos que diseñar, revisar y mantener antes de enviar algo a producción
* **Fricción en integración** → las abstracciones de DDD no se ajustan a las necesidades de infraestructura, y complican la integración
* **Menor flexibilidad** → el código de infraestructura debe evolucionar mediante experimentación y ajustes; los modelos rígidos ralentizan la iteración

👉 Para los módulos que deben resolver un problema tecnológico, estos costes superan con creces cualquier beneficio. Es mejor usar los patrones y paradigmas que mejor se ajusten a las necesidades del problema.

---

## 3. El Error Común: Convertir DDD en un estándar

* Razonamiento: *“Como nuestra compañía tiene una importante carga de lógica de negocio compleja, vamos a usar DDD en todos los proyectos.”*
* Realidad: Solo un subconjunto concreto e identificable de los proyectos se relaciona directamente con esa lógica de negocio compleja, el resto resuelven problemas puramente técnicos.
* Resultado: 
  * entregas más lentas
  * complejidad innecesaria
  * deuda técnica
  * esfuerzo desperdiciado

---

## 4. La Solución: DDD Selectivo

* Aplicar DDD **solo en los módulos donde la complejidad de negocio lo hace necesario. y sólo aquellas prácticas de DDD que realmente aporten valor dadas las características concretas del proyecto.**

* *“DDD works best when used judiciously — and struggles when forced on projects that don't need its full rigor”* — [Interview Noodle](https://interviewnoodle.com/why-domain-driven-design-is-more-than-just-a-buzzword-c8305cd8bec0?utm_source=chatgpt.com)
* *“Using DDD for simple domains is thus an overkill, you'd only be shooting yourself in the foot”* — [Reddit /r/java](https://www.reddit.com/r/java/comments/n0kukj/is_domain_driven_design_still_the_recommended/?utm_source=chatgpt.com)

---

## 5. Recomendación Práctica

### Checklist: ¿Este proyecto necesita DDD?

* ¿Existen **invariantes de negocio no triviales** que siempre deben cumplirse?
* ¿Las reglas de negocio cambian de forma frecuente o importante?

✅ Si no se cumplen esas 2 condiciones probablemente DDD **no compense**.

👉 El enfoque correcto es la **adopción selectiva**:

* Usa DDD **solo** en los proyectos (o módulos) donde la complejidad de negocio lo justifique.
* Aplica **solo las partes de DDD** que aporten valor.
* En proyectos centrados en infraestructura, usa patrones más simples y probados.

---

## 6. El lenguaje ubicuo no es exclusivo de DDD.

No necesitas DDD para tener lenguaje ubicuo.
Puedes establecer un vocabulario compartido y consistente incluso en un código espagueti — solo es cuestión de consensuar nombres y usarlos siempre igual. 

No necesitas bounded contexts, agregados, invariantes ni tres capas de abstracciones solo para solucionar la terminología.

Si quiero un vaso de leche, no necesito comprar una vaca.

Y la misma lógica se aplica dentro de DDD:

* Un proyecto puede beneficiarse de **bounded contexts**, pero eso no significa que también necesite **agregados**.
* Un proyecto puede beneficiarse de **invariantes**, pero eso no significa que también necesite **CQRS o event sourcing**.
* Un proyecto puede beneficiarse de **agregados**, pero eso no significa que también necesite **capas extra de abstracción ni domain events**.

👉 Debe evaluarse la conveniencia de cada táctica DDD para cada proyecto en función de lo que le aporta y de lo que cuesta. 

---

## 7. Conclusión

DDD es una herramienta poderosa, pero no universal.
Ha probado su utilidad allá donde la complejidad de negocio es alta, pero también ha demostrado ser una carga cuando se fuerza su uso donde no es necesario.

👉 La lección de la era de los microservicios es clara: **no conviertas una buena idea en un mal estándar.**
Aplica DDD solo donde la complejidad de negocio lo demande, y únicamente las partes que aporten valor. En el resto aplica aquellos patrones y paradigmas que tengan sentido para el problema concreto. 

