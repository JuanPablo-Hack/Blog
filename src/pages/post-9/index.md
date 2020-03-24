---
path: "/post-9/"
category: "NodeJS"
tags: ["tag"]
title: "Crea tu servidor web con ExpressJS"
date: "2020-03-20T15:52:00.000Z"
summary: "En este tutorial vamos a ver como levantar un servidor web utilizando el modulo de Express..."
components: [{
  rootId: 'sample-component',
  fileName: 'sample',
}]
images: ["images/exp.jpeg"]
---

> La demanda de programadores de Backend en el mercado es muy alta, por lo que es necesario saber como es su estructura

En el tutorial de hoy vamos a levantar un servidor con NodeJS utilizando el modulo expressJS, vamos a ver como configurar el servidor y declararle las rutas con las que vamos a visualizar las paginas de renderizacion.
Para comenzar vamos a crear nuestro entorno de trabajo en mi caso lo llamare, servidor-express, usted puede llamarlo con el nombre de su preferencia, entonces creamos el directorio:

```js
mkdir servidor-express
```

Una vez realizado esto vamos a abrir el directorio con el editor de texto de su preferencia en mi caso vamos a utilziar Visual Studio Code, y lo hacemos de la siguiente manera:

```js
code servidor-express/
```

#### Iniciando el proyecto con NodeJS

Una vez ya en el editor de texto, abriremos una linea de comandos integrada, en el caso de Visual Studio Code es Ctrl+Shtf+', una vez ya abierta la terminal vamos a iniciar un proyecto con NodeJS, de la siguiente manera:
 
```js
npm init --yes
// Respuesta de la terminal
Wrote to /home/pablo/servidor-express/package.json:

{
  "name": "servidor-express",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```
El comando anterior inicializo el proyecto en NodeJS el cual nos arroja un documento .json con la configuracion de nuestro proyecto 

#### Instalando ExpressJS en el directorio

Express.js, o simplemente Express, es un marco de aplicación web para Node.js, lanzado como software gratuito y de código abierto bajo la Licencia MIT. Está diseñado para crear aplicaciones web y API. Se le ha llamado el marco de servidor estándar de facto para Node.js.d

Entonces vamos a instalarlo de la siguiente forma: 

```js
npm i express
//Respuesta de la terminal
npm notice created a lockfile as package-lock.json. You should commit this 
file.
npm WARN servidor-express@1.0.0 No description
npm WARN servidor-express@1.0.0 No repository field.

+ express@4.17.1
added 50 packages from 37 contributors and audited 126 packages in 18.684s
found 0 vulnerabilities
```
Una vez hecho esto, ahora solo vamos a preparar nuestro entorno de desarrollo vamos a crear una carpeta llamada scr donde estara el archivo index.js donde se ejecutara el servidor y dentro de src vamos a crear una carpeta routes con las rutas con las que respondera el servidor.

```js
    .
    ├── node_modules
    ├── src
        ├── index.js
    ├── package.json
```
Ahora solo nos queda cofigurar el servidor entonces vamos al archivo que ya creamos en src/index.js y vamos a escribir el siguiente codigo:

```js
//Mandamos llamar el modulo de express y lo guardamos como express
const express = require('express')
//Declaramos el servidor
const app = express()
//Rutas
app.get('/',(req,res)=>{
    res.send('Hola mundo')
})

//Iniciamos el servidor en el puerto 3000
app.listen(3000,()=>{
    console.log('Servidor en el puerto 3000')
})
```
Ahora lo unico que tenemos que hacer es ejecutar el script de index.js para correr el servidor

```js
node scr/index.js
```

Ahora para comprobar que todo a ido bien vamos a http://localhost:3000/ y comprobamos que nuestro servidor nos haya dado una respuesta con una pagina que diga Hola Mundo

Hasta este punto ya tienes tu servidor para comenzar con el backend de tu aplicacion en los siguientes tutoriales veremos como elaborar una API con formatos JSON.