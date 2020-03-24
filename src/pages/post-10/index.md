---
path: "/post-10/"
category: "NodeJS"
tags: ["tag", "tag-3"]
title: "Instalacion de Node JS"
date: "2020-03-20T13:08:00.000Z"
summary: "Seguiremos paso a paso la instalacion de NodeJS y NPM en ubuntu..."
images: ["images/node.jpeg"]
---

> En la actualidad la web se esta volviendo una herramienta muy importante para las empresas, por lo que herramientas y plataformas surgen

Node.js es un entorno en tiempo de ejecución multiplataforma, de código abierto, para la capa del servidor basado en el lenguaje de programación ECMAScript, asíncrono, con E/S de datos en una arquitectura orientada a eventos y basado en el motor V8 de Google. Vamos a comenzar instalando NodeJS con el siguiente comando desde la terminal de Ubuntu 18.04:

```js
sudo apt install node
```

Despues de haber instalado NodeJS en su version mas reciente vamos a instalar el gestor de paquetes, ya sea NPM o YARN eso es a gusto del programador pero igual vamos a ver ambas formas para que puedas elegir ambas:

#### NPM

NPM es el sistema de gestión de paquetes por defecto para Node.js, un entorno de ejecución para JavaScript, bajo Artistic License 2.0.

```js
npm install npm@latest -g
```

#### YARN

Yarn es un nuevo tipo de instalador de paquetes JavaScript y gestor de dependencias lanzado por la empresa Facebook en colaboración con otros desarrolladores como Google donde introduce cambios en esa gestión de dependencias, en la ejecución de tareas y algunas mejoras de rendimiento, también en el cambio de enfoque en la descarga e instalación de los paquetes y en su gestión de las dependencias, por ejemplo, con Yarn el programador podrá gestionar nuestras dependencias con mayor fiabilidad

Primero deberá configurar el repositorio: 

```js
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
```
Entonces puedes simplemente:

```js
sudo apt update && sudo apt install yarn
```

Para poder finalizar ahora solo debemos de verificar que se ha instalado todo correctamente checando las versiones de los paquetes que hemos instalado y la version de NodeJS instalada.
Una vez dicho esto haremos lo siguiente:

```js
node -v
//La version de node
v10.19.0
npm -v
//La version de npm
6.14.3
```

Y lanzamos el comando node para ejecutar comandos de JS

```js
node
> 5+4
9
> 8*4
32
> console.log('Hola mundo')
Hola mundo
```
Hasta este punto ya tienes NodeJS para comenzar a trabajar con servidores web y aplicaciones moviles, en el siguiente tutorial veremos como levantar un servidor con ExpressJS.
