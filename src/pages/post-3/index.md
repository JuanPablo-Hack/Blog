---
path: "/post-3/"
category: "NodeJS"
tags: ["tag"]
title: "Crear un blog con Gatsby CLI"
date: "2020-03-22T00:15:00.000Z"
summary: "En el tutorial de hoy vamos a aprender a crear un blog con Gatsby CLI..."
images: ["images/1.jpg"]
---

## Instalacion

En el tutorial de hoy vamos a aprender a crear un blog con Gatsby CLI, primero lo primero vamos a necesitar instalar la herramienta de Gatsby CLI dentro de nuestra computadora, para eso ya debemos de tener NodeJS y npm o yarn para poder llevar a cabo nuestro proyecto, entonces ya dicho esto vamos a comenzar a por instalar Gatsby con el siguiente comando:

```js
npm install -g gatsby-cli
```
## Creacion del sitio 

Entonces se comienza a instalar el paquete de instalacion de Gatsby para comenzar con nuestro blog, entonces ya teniendo el entorno de trabajo vamos a crear un blog de la siguiente forma:

```js
gatsby new primer-blog
```
Ya creado nuestro blog nos vamos a ir al directorio para poder comenzar a trabajar con el, entonces vamos a directorio:

```js
cd new primer-blog
```
## Iniciando el servidor

Para comenzar a ver nuestro blog, solo tenemos que empezar la ejecucion de desarrollo con:

```js
gatsby develop
```
Gatsby iniciará un entorno de desarrollo de recarga en caliente accesible de forma predeterminada en http://localhost:8000.



Intente editar las páginas de JavaScript en src / pages. Los cambios guardados se recargarán en vivo en el navegador.

### Entorno de produccion

```js
gatsby build
```
Gatsby realizará una compilación de producción optimizada para su sitio, generando paquetes de código HTML estático y JavaScript por ruta.

Vemos que gatsby es un gran motor para poder crear un blog de una manera muy rapida y sencilla, si sabes codigo y un poco de markdown en poco tiempo tienes la oportunidad de crear blogs muy dinamicos.