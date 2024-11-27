---
layout: post
title: "Proyecto: Sistema Distribuido"
categories: project, design
---

Idea: sistema totalmente distribuido para aprender cómo funciona un sistema sin una central.<!--more-->

# Descripción

Esta aplicación que maneja nodos en una red distribuida. Permite registrar nodos, sincronizar la lista de nodos conocidos, y verificar la actividad de un nodo. Además, ofrece información sobre el nodo actual y la red de nodos conectados. Usa una lista de nodos semilla para iniciar la conexión y actualizar periódicamente los nodos conocidos. La comunicación con otros nodos se hace a través de solicitudes HTTP, con endpoints para obtener, agregar y sincronizar nodos.

## Diagrama

<pre class="mermaid">
graph TD
    A[Seed Node] --> B[Node 1]
    A --> C[Node 2]
    B --> D[Node 3]
    B --> E[Node 4]
    C --> F[Node 5]
    C --> G[Node 6]
    D --> H[Node 7]

    %% Actor externo solicitando la lista de nodos a Node 3

    D -->|Devuelve Lista de Nodos| X
    F -->|Devuelve Lista de Nodos| X

</pre>

# ¿Qué debe hacer un sistema?

- Debe implementar todo lo necesario para descubrir los demás componentes (Nodos) en la red.
- Debe poder listar todos los Nodos en la red.

# Definición

## Peer

### Inicio del Nodo

El nodo inicia su proceso.

### Conectar al Nodo Semilla

Intenta conectarse al nodo semilla para obtener la lista inicial de nodos.

### Obtener Lista de Nodos

Si tiene éxito, agrega los nodos conocidos a su lista.

### Sincronizar Periódicamente

Establece una sincronización periódica para comunicarse con otros nodos.

### Ping a Nodos Conocidos

Verifica si los nodos están activos.

### Enviar Lista Actualizada

Comparte la lista actualizada con otros nodos.

### Actualizar o Eliminar Nodos

Actualiza la lista con nuevos nodos o elimina nodos inactivos.

<pre class="mermaid">
graph TD
    A[Inicio del Nodo] --> B(Conectar al Nodo Semilla)
    B -->|Exitoso| C[Obtener Lista de Nodos]
    B -->|Fallido| D[Esperar y Reintentar]

    C --> E(Agregar Lista de Nodos Conocidos)
    E --> F[Sincronizar Periódicamente]

    F --> G(Ping a Nodos Conocidos)
    F --> H(Enviar Lista Actualizada a Nodos)
    G -->|Ping Exitoso| I[Actualizar Lista]
    G -->|Ping Fallido| J[Eliminar Nodo Inactivo]

    H --> K[Recibir Nueva Lista]
    K --> E

    I --> E
    J --> E

</pre>

# Startup de cada Nodo

## Inicio de la aplicación:

El nodo inicializa el servidor Express y configura los endpoints necesarios.

- GET `/nodes`: Retorna la lista actual de nodos conocidos.
- POST `/nodes`: Registra nuevos nodos.
- GET `/ping`: Indica que el nodo está funcionando.
- GET `/ping`: Muestra la información de nodo.
- GET `/network`: Retorna los datos de todos los nodos en la red.

## Conexión al nodo semilla:

El nodo intenta conectarse al nodo semilla para obtener la lista de nodos conocidos.

- Si la conexión es exitosa:
  Recibe la lista de nodos del nodo semilla.
  Agrega los nodos recibidos a su lista local de nodos conocidos.
- Si la conexión falla:
  Muestra un error en consola.
  Reintenta la conexión automáticamente en el siguiente ciclo de sincronización.

## Registrar otros nodos:

Al recibir una solicitud POST `/nodes` de un nuevo nodo:

- Agrega el nodo a la lista de nodos conocidos si aún no está.
- Retorna la lista actualizada al nuevo nodo.

## Sincronización periódica (cada 30 segundos):

Envía solicitudes GET `/nodes` a todos los nodos conocidos.
Recibe y fusiona las listas de nodos, eliminando duplicados.
Si no puede contactar a un nodo, lo marca como inactivo en consola, pero mantiene su URL por si vuelve a estar disponible.

## Verificación de actividad de nodos:

Otros nodos pueden verificar si este nodo está activo mediante el endpoint GET `/ping`.
Retorna una respuesta indicando que el nodo está activo.

# Ejemplo en Javascript

```Javascript
// Importar dependencias
import express from 'express';
import fetch from 'node-fetch';

// Inicializar la aplicación Express
const app = express();
app.use(express.json());

// Url del Nodo (la forma de identificarlo)
const nodeUrl = process.env.NODE_URL;
// Nombre del Nodo (la forma de identificarlo)
const nodeName = process.env.NODE_NAME ?? 'unknown name';
// Iniciar el servidor en el puerto 3000
const port = process.env.PORT || 3000;
// Nodo semilla
const seedNodeUrls = process.env.SEED_NODE_URLS || '';

// Tiempo entre cada actualización
var refreshTime = 60 * 60 * 1000 // 1 hora

// Lista en memoria de nodos conocidos
let knownNodes = seedNodeUrls ? [...seedNodeUrls.split(',')] : [];

/************ BEGIN internal functions ************/

// Función que devuelve toda la info de este nodo
function myInfo() {
    return {
        name: nodeName,
        version: '0.0.1'
    };
}

// Función para registrar el nodo en el semilla
async function registerNode() {
    knownNodes.forEach(async (seedUrl) => {
        try {
            const response = await fetch(`${seedUrl}/nodes`, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({ nodeUrl }),
            });
            if (response.ok) {
                console.log(`Nodo registrado: ${nodeUrl}`);
            } else {
                console.error('Error al registrar el nodo:', response.statusText);
            }
        } catch (error) {
            console.error('Error al registrar el nodo:', error);
        }
    });
}

// Sincronizar nodos conocidos periódicamente
function syncNodes() {
    console.log("Sincronizando...")
    console.log("Nodos conocidos:", knownNodes);
    knownNodes.forEach(async (nodeUrl) => {
        try {
            console.log("Sincronizando con el nodo", nodeUrl);
            const response = await fetch(`${nodeUrl}/nodes`);
            const newNodes = await response.json();
            knownNodes = [...new Set([...knownNodes, ...newNodes])];
        } catch (error) {
            console.error(`Error sincronizando con el nodo ${nodeUrl}: ${error.message}`);
            if (knownNodes.lengh !== 0) {
                knownNodes = [...knownNodes.filter(x => x !== nodeUrl)];
            }
        }
    });
}
/************ END internal functions ************/

/************ BEGIN endpoints ************/

// Endpoint GET /nodes - Retorna la lista de nodos
app.get('/nodes', (req, res) => {
    res.json(knownNodes);
});

// Endpoint POST /nodes - Registra un nuevo nodo
app.post('/nodes', (req, res) => {
    const { nodeUrl } = req.body;
    console.log('Agregando el nodo', nodeUrl);
    if (!knownNodes.includes(nodeUrl) && nodeUrl !== nodeUrl) {
        knownNodes.push(nodeUrl);
    }
    console.log("Nodos conocidos:", knownNodes);
    res.status(201).json({ message: 'Nodo agregado', knownNodes });
});

// Endpoint GET /ping - Verifica si el nodo está activo
app.get('/ping', (req, res) => {
    res.json({ message: 'Nodo activo' });
});

app.get('/info', (req, res) => {
    res.json(myInfo());
});

app.get('/network', async (req, res) => {
    var rst = [myInfo()];
    for (let i = 0; i < knownNodes.length; i++) {
        const response = await fetch(`${knownNodes[i]}/info`);
        rst = [...rst, await response.json()];
    }
    res.json(rst);
});

/************ END endpoints ************/

setInterval(syncNodes, refreshTime);

app.listen(port, async () => {
    console.log(`Servidor ${nodeName} iniciado en ${nodeUrl}`);
    console.log(`Seeds registrados ${seedNodeUrls}`);
    // Registrar el nodo en el seed después de que el servidor se inicie
    await registerNode();
    syncNodes(); // Conectar al nodo semilla al iniciar
});

```

  <script type="module">
    import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.esm.min.mjs';
    mermaid.initialize({ startOnLoad: true });
  </script>
