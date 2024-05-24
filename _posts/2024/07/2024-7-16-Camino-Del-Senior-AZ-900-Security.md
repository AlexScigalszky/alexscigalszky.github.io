---
layout: post
title: "AZ-900 Curso de Azure: Security"
categories: ["senior"]
---

La seguridad en Azure es muy importante, podemos ver:<!--more-->:

# Defence in Depth

La defenza en Azure está definida en diferentes niveles dependiendo el tipo de sistema:

## Servidores on-promise

- Fisico. Seguridad del edificio, hardward y personal.
- Líneas de defensa. Diferentes niveles como tarjetas de acceso, puertas, guardias, firewalls, etc.
- Todo debe administrarse desde la empresa.

## Servidores en Azure

Hay 7 niveles de seguridad:

1. Fisico. Autorización para el acceso físiso.
2. Identity y Access. Autorización y autenticación.
3. Perimeter. Protección ante ataques DDOS.
4. Network. Filtro contra el tráfico y la seguridad estándar de internet.
5. Compute. Proteje contra intrusos a los servidores y bases de datos.
6. Gateways y Firewalls. Proteje las aplicaciones sobre Azure.
7. Data. La información es encriptada para todos aquellos que no poseen acceso.

# Securing Network Connectivity

Para protejer la red, Azure usa un firewall.

## Firewall

- Tiene un set de reglas para permitir o negar paquetes de red.
- Existen muchas variantes, para pequeñas o grandes redes.
- Todas las redes que requieran seguridad, tendrán un firewall.

## Distributed Denial of Service (DDoS)

Muchas peticiones (el record fué de 127millones de peticiones por segundo) a la misma vez a un mismo servicio.
Azure va a proteger sin dar de baja el servicio.

## Network Security Group (NSG)

Es un recurso que viene junto con las redes virtuales, redes o subredes.
Determina quién puede o no ingresar a esa red basandose en las reglas de inbound y outbound.

## Application Security Group

Otro recurso exclusivo para proteger aplicaciones.

# Public and Private Endpoints

Los servicios PaaS (o virtual networks) son accesibles de forma pública por defecto.
Para proteger esos recursos existen dos opciones:

| Aspecto               | Service Endpoints                            | Private Endpoints                                     |
| --------------------- | -------------------------------------------- | ----------------------------------------------------- |
| Conectividad          | Extiende la red virtual a servicios de Azure | Proporciona acceso privado a un servicio de Azure     |
| Dirección IP          | Usa direcciones IP públicas del servicio     | Usa direcciones IP privadas en la red virtual         |
| Acceso desde VNet     | Sí                                           | Sí                                                    |
| Acceso desde Internet | No                                           | No                                                    |
| Seguridad             | Asegura el tráfico entre VNet y servicio     | Asegura el tráfico y limita la exposición al Internet |
| Recursos soportados   | Amplio conjunto de servicios de Azure        | Limitado a ciertos servicios de Azure                 |
| Administración        | Configurado a nivel de servicio en Azure     | Configurado a nivel de recurso en Azure               |

# Microsft Defender for Cloud

Es un portal para manejar la seguridad en el portal de azure.

- Provee todas las alertas.
- Permite todas las arquitecturas.
- Muestra las reglas y sus buenas prácticas.

Para usarlo hay que:

1. Definir las restricciones
2. Proteger los recursos.
3. Responder a las alertas que Microsft Defender for Cloud muestra

# Azure Key Vault

Sirve para guardar y compartir las contraseñas encriptadas fuera del alcance de todo.
Ventajas:

- Hardward seguro.
- Applicaciones Aisladas.
- Escala globalmente.

# Azure Information Protection

asegura la información, mails, o datos que salgan de la empresa. Se puede clasificar la información entre diferentes categorías, trackear lo que pasa con los datos, compartir información de forma segura y controlar la integraciones de documentos con herramientas de terceros. Por ejemplo: enviar un email con el tag "Azure Information Protection" para que llegue de forma segura (encripta y chequea el usuario).

# Azure Sentinel (SIEM)

Herramienta para detectar comportamiento inusuario, lo integra con otros recusos de azure para tomar medidas.
Los pasos de acción son:

1. Recolección de datos.
2. Agrega la información y la normaliza.
3. Analiza y busca ataques.
4. Un ataque pasa.
5. Realiza acciones para mejorar.

# Azure Dedicated Host

Es un server completamente aislado y controlado por el usuario (pero otorgado por azure). Sólo el usuario puedo tocarlo.
El usuario tiene control de las actualizaciones. Se puede instalar cualquier SO.

# Microsoft Defender for Identity

Como los usuario son el eslabon más debil en una organización.
Microsoft:

- Monitorea usuarios
- Registra el comportamiento anormal
- Sugiere cambios
