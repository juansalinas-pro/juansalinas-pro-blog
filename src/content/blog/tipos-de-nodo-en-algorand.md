---
title: Tipos de nodos en Algorand
author: Juan
pubDatetime: 2024-12-06T15:57:52.737Z
slug: tipos-de-nodo-en-algorand
featured: true
ogImage: ""
tags:
  - blockchain
  - web3
  - algorand
description: Los dos tipos de nodos que componen la red de Algorand
---

La red de Algorand se compone de dos tipos de nodos. A continuación, se detallan las diferencias y características de cada uno.

---

## **Nodos “non-relay” (Nodos de participación)**

- Responsabilidad:  
  Contribuyen a la red proponiendo y validando bloques, participando en el protocolo de consenso. Por ello, también se les llama “nodos de participación”.

- Conexiones:
  - No se conectan directamente entre sí.
  - Se conectan exclusivamente a los nodos “relay”.
  - Pueden comunicarse con varios nodos “relay” simultáneamente.

---

## **Nodos “relay”**

- Función:  
  Son la columna vertebral de la comunicación en la red Algorand.

- Comunicación:
  - Se comunican entre sí y enrutan bloques a todos los nodos de participación conectados.
  - Optimizan la red al encontrar las rutas más eficientes, reduciendo bucles de comunicación entre nodos de participación.

---

A continuación veremos un ejemplo de topología de la red de Algorand a modo de aportar mayor claridad:
![something](@assets/images/tipos-de-nodos-en-algorand.webp)

---

## **Configuraciones posibles de nodos**

Los nodos pueden configurarse como:

- **“Archival”**: Almacenan toda la blockchain.
- **“Non-archival”**: Solo almacenan los últimos 1000 bloques.

### Notas:

- Los nodos “relay” siempre son **“archival”**.
- Los nodos de participación **“archival”** suelen utilizarse para alimentar un indexador, permitiendo consultas avanzadas sobre el historial de la blockchain.
- Los nodos de participación no necesitan ser del tipo “archival”.
- Para mitigar riesgos y ataques, se recomienda usar los nodos de participación exclusivamente para el protocolo de consenso.

---

## **Casos de uso y configuraciones recomendadas**

### 1. **Participar del protocolo de consenso y contribuir a la seguridad de la red Algorand**

- Configuración:  
  **“Non-relay” (nodo de participación)** + **“Non-archival”**
- Detalles:
  - Se necesita poseer algunos ALGO.
  - Es crucial monitorear el nodo 24/7 para garantizar su correcto funcionamiento.

### 2. **Enviar transacciones y leer el estado actual de los smart contracts**

- Configuración:  
  **“Non-relay”** + **“Non-archival”** + _(no ser nodo de participación)_
- Ejemplo de uso:
  - Un sitio web de dApp que no utiliza datos históricos.
  - Un sitio que muestra saldos de cuentas importantes.

### 3. **Acceso completo a datos históricos con consultas avanzadas**

- Configuración:  
  **“Non-relay”** + **“Archival”** + **Indexer** + _(no ser nodo de participación)_

### 4. **Obtener pruebas de estado (“state proof”) para cualquier bloque**

- Configuración:  
  **“Non-relay”** + **“Archival”** + _(no ser nodo de participación)_

---

## **Referencias**

[Documentación oficial de Algorand](https://developer.algorand.org/docs/run-a-node/setup/types/)
