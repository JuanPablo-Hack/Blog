---
path: "/post-7/"
category: "Go"
tags: ["tag"]
title: "Servidor con GorillaMux"
date: "2020-03-21T17:31:00.000Z"
summary: "Crea tu servidor web con go de la manera mas rapida y sencilla"
images: ["images/gomux.jpeg"]
---

En el tutorial de hoy vamos a aprender como levantar un sevidor web con el lenguaje de programacion Go, con el modulo de Gorilla Mux, para comenzar debemos tener en cuenta que tenemos que tener instalado Go en nuestro sistema operativo de no ser asi, puedes buscar el tutorial e instalarlo, todo ya dicho vamos a comenzar.

Para empezar vamos a crear un directorio o nuestro espacion de trabajo para comenzar a trabajar en nuestro servidor web:

```js
mkdir servidor-go
```
Vamos abri nuestro espacio de trabajo en el editor de texto de su preferencia, en mi caso voy a utilizar Visual Studio Code, asi que vamos a trabajar en este editor de texto, una  vez ya abierto el editor de texto vamos a importar el paquete de gorilla mux a nuestro proyecto

```js
go get github.com/gorilla/mux
```
Ahora vamos a escribir nuestro codigo creando un archivo de main.go recuerden que ese sera el archivo que va a compilar o interpretar go de esta forma vamos a escribir lo siguiente:
```js
package main

import (
	"fmt"
	"net/http"
	"github.com/gorilla/mux"
)
```
Aqui solo estamos importando todos los paquetes de Go que vamos a utilizar, ahora vamos a comenzar a declarar el servidor de la siguiente forma:
```js
func main() {
	//Iniciamos el servidor
	router := mux.NewRouter().StrictSlash(true)
	//Mandamos llamar a las rutas
	router.HandleFunc("/", homeLink)
	router.HandleFunc("/event", createEvent).Methods("POST")
	router.HandleFunc("/events", getAllEvents).Methods("GET")
	router.HandleFunc("/events/{id}", getOneEvent).Methods("GET")
	log.Fatal(http.ListenAndServe(":3000", router))

}
```
Ahora solo vamos a crear la ruta de la pagina inicial, como en el ejemplo de NodeJS vamos a rederizar la ruta inicial con un Hola mundo y esto lo haremos escribiendo el siguiente codigo: 
```js
func homeLink(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintf(w, "Hola mundo desde Gorilla Mux")
}
```
Entonces una vez ya hecho esto ejecutamos el servidor con el siguiente comando:
```js
go run main.go
```
Nos vamos a http://localhost:3000/ y vamos a comprobar que nuestro servidor ya se encuentra activo y veremos el mensaje de "Hola mundo desde Gorilla Mux"


