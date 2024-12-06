---
title: ¿Qué son los ADRs?
author: Juan
pubDatetime: 2024-11-06T15:57:52.737Z
slug: que-son-los-adrs
featured: true
ogImage: ""
tags:
  - software
  - engineering
description: Un proceso para documentar las decisiones arquitectónicas
---

# Registro de decisiones arquitectónicas (ADRs)

## Un proceso para documentar las decisiones que toma el equipo sobre un aspecto importante de la arquitectura de software que planea crear.

---

### ADRs (Architectural Decision Records)

Los ADRs son descripciones de texto breve que documentan decisiones importantes de arquitectura durante el ciclo de vida del desarrollo de software. Los ADRs incluyen un contexto para cada decisión, las opciones consideradas, las ventajas y desventajas de las opciones y finalmente la decisión tomada por el equipo.

---

### Beneficios de los ADRs

- **Alinea a los equipos sobre decisiones importantes:** Los ADRs pueden ser accesibles de forma pública en toda la compañía, de tal forma que sea fácil alinear a los equipos y comunicar las decisiones.

- **Un registro que perdura en el tiempo:** Cuantas veces ha pasado que las decisiones son tomadas en reuniones de forma rápida sin quedar registros asentados sobre el mismo, o son decisiones tomadas por una sola persona, o el equipo cambia, o los miembros dejan la compañía. Los ADRs nos brindan una forma fácil y rápida para registrar estas decisiones.

- **Contexto para los nuevos miembros:** Brinda una fuente de decisiones tomadas antes que los nuevos miembros se sumen al equipo.

---

### Estructura de un ADR

Un ADR puede ser personalizado incluyendo toda la información que necesites, pero existen plantillas como la siguiente:

- **Title:** Un título descriptivo, que generalmente es el mismo nombre del archivo del ADR.
- **Status:** El estado actual, ejemplos: proposed, accepted, rejected, deprecated, superseded.
- **Context:** Una descripción de la situación o problema que conduce a tomar esta decisión, se agregan todos los detalles necesarios para entender el contexto.
- **Decision:** Describe brevemente la decisión tomada y las razones.
- **Consequences:** Cualquier consecuencia positiva y negativa que tenga esta decisión en otras partes de la arquitectura.

---

### Ejemplo real de ADR

```md
# GraphQL Framework

- **Status**: accepted
- **Deciders**: Obi-Wan Kenobi, Qui-Gon Jinn, Anakin Skywalker
- **Date**: 01/06/2015

## Context and Problem Statement

Currently there is a REST API that groups all the company's data about cities, countries, provincies, in a MongoDB Database, every entity has its endpoint.

When a client needs to merge informations from more than one entity it should make several requests to several endpoints, also the client has the responsibility of handeling the request errors from the several endpoints.

Additionally, the client doesn't have the capability to define the response fields, so this scenario can lead to underfetching/overfetching data.

## Decision Drivers

- We need a component responsible for making several requests to the several endpoints, merge the data, so the client can make only one request.
- We need a component that can allow to the client to define the data or fields of the response that it needs to avoid underfetching/overfetching.
- We need a library/framework base on Spring Boot.

## Considered Options

- [GraphQL Java](https://www.graphql-java.com/)
- [GraphQL Java Kickstart](https://www.graphql-java-kickstart.com/)
- [DGS](https://netflix.github.io/dgs/getting-started/)

## Decision Outcome

Chosen option: DGS, because the framework has really good documentation and good samples on its GitHub repo, and it is supported by a well known company, Netflix.

### Positive Consequences

- Good documentation
- Supported by a well known company
- Project with several contributors

### Negative Consequences

## Pros and Cons of the Options

### GraphQL Java

- Good, because the Spring team engineering collaborates to support this library: https://spring.io/projects/spring-graphql
- Good, because it has a good documentation and a repo with samples: https://github.com/spring-projects/spring-graphql/tree/main/samples
- Good, because the implementation is mostly base on an annotation-based programming model, so you can run a simple GraphQL server quickly.
- Bad, because too many lines of code are written for custom exceptions handling.
- Bad, because too many lines of code are written for advanced implementations (context, tracing, metrics and logging)

### GraphQL Java Kickstart

- Good, because it has a video course that shows how to use the library and best practices for GraphQL servers.
- Good, because it has a easy implementation to handle exceptions, base on Spring @ExceptionHandler annotation.
- Bad, because too many lines of code are written for advnced implementations.
- Bad, because it doesn't have a good documentation and is not updated.
- Bad, because there isn't a well knowns company behind the project.
- Bad, because the project is maintain by a small team and they ask for people to join them.
- Bad, beacuase the library doesn't have a annotation-based programming model entirely.
- Bad, because too many lines of code are written for advanced implementations (context, tracing, metrics and logging)

### DGS

- Good, because it has a really good documentation and a repo with samples in Kotlin: https://github.com/Netflix/dgs-examples-kotlin
- Good, is a framwork supported by Netflix and the project has several contributors.
- Good, because the implementation is mostly base on an annotation-based programming model, so you can run a simple GraphQL server quickly.
- Good, because it makes simpler advanced implementations (context, tracing, metrics and logging)
- Bad, because too many lines of code are written for custom exceptions handling.
```

---

### Herramientas para administrar ADRs

- [adr-manager](https://github.com/adr/adr-manager)
- [adr-viewer](https://github.com/mrwilson/adr-viewer)
- [ADR templates](https://github.com/joelparkerhenderson/architecture-decision-record#adr-example-templates)
- [Loqbooq](https://loqbooq.app/)
- [Log4Brains](https://github.com/thomvaill/log4brains)

---

### Fuentes

- [Sitio oficial ADR](https://adr.github.io/)
- [Guía AWS sobre ADRs](https://docs.aws.amazon.com/es_es/prescriptive-guidance/latest/architectural-decision-records/welcome.html)
