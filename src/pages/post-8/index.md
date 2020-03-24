---
path: "/post-8/"
category: "Go"
tags: ["tag"]
title: "Instalacion de Go en Linux"
date: "2020-03-20T19:30:00.000Z"
summary: "Instalacion y configuracion de Go en Ubuntu 18.04"
images: ["images/go.jpeg"]
---

> Go se ha hecho un lenguaje de programacion demasiado popular en la actualidad por su rapidez de ejecucion y su sintaxis

Go es un lenguaje de programación concurrente y compilado inspirado en la sintaxis de C, que intenta ser dinámica como Python y con el performance de C o C++. Ha sido desarrollado por Google, y sus diseñadores iniciales fueron Robert Griesemer, Rob Pike y Ken Thompson.

En este tutorial vamos a instalar go y como siempre hacemos iremos paso a paso explicando el por que de todas las acciones que se van realizando, entonces vamos a comenzar por instalar Go con el siguiente comando:

```js
sudo apt install go
```
Una vez ya instalado para comprobar que todo salio bien vamos a ejecutar en la terminal:

```js
go version
//Respuesta de la terminal
go version go1.10.4 linux/amd64

```
Con eso ya podemos garantizar que hemos utilizado bien, bueno ahora haremos nuestro primer programa que seria un hola mundo, para eso vamos a abrir un editor de texto y crear un archivo con el formato .go, en mi caso yo llamare al archivo 
Holamundo.go y donde pondremos lo siguiente:

```js
package main

import "fmt"

func main() {
	fmt.Println("Hola Mundo")
}
```
Por ultimo vamos a ejecutar nuestro script de Go con el siguiente comando:

```js
go run Holamundo.go
//Repuesta de la terminal
Holamundo
```
