---
path: "/MongoDB/"
category: "Bases de Datos"
tags: ["tag", "tag-2"]
title: "Bases de datos Documentales con MongoDB"
date: "2020-04-01T17:48:00.000Z"
summary: "Veremos la definicion de una base de datos documental y MongoDB"
images: ["images/mg.jpeg"]
---

# Bases de Datos Documental

Una base de datos documental está constituida por un conjunto de programas que almacenan, recuperan y gestionan datos de documentos o datos de algún modo estructurados. Este tipo de bases de datos constituyen una de las principales subcategorías dentro de las denominadas bases de datos NoSQL. A diferencia de las bases de datos relacionales, estas bases de datos están diseñadas alrededor de una noción abstracta de "Documento". 

## Los documentos

El concepto central de una base de datos orientada a documentos es el concepto mismo de Documento. Mientras cada implementación de base de datos orientada a documentos difiere en los detalles, en general todas ellas comparten el principio de que los documentos encapsulan y codifican datos o información siguiendo algún formato estándar. Entre las codificaciones usadas en la actualidad se encuentran XML, YAML y JSON, así como formatos binarios como BSON.

Los documentos dentro de una base de datos orientada a documentos son similar, de algún modo, a registros, tuplas o filas en una base de datos relacional pero menos rígidos. No se les requiere ajustarse a un esquema estándar ni tener todos las mismas secciones, atributos, claves o cosas por el estilo. Por ejemplo un documento puede ser: 

```js
 {
    Nombre:"Pepe",
    Dirección:"Plaza Mayor 5",
    Profesión:"Panadero"
 }
```
## Organizacion

Las distintas implementaciones de bases de datos documentales que podemos organizan los documentos de muy distintas formas, entre las que se encuentran:

1. Colecciones
2. Etiquetas
3. Metadatos ocultos
4. Jerarquías de directorios

# MongoDB

Se trata de una base de datos creada por 10gen del tipo orientada a documentos, de esquema libre, es decir, que cada entrada puede tener un esquema de datos diferente que nada tenga que ver con el resto de registros almacenados. Es bastante rápido a la hora de ejecutar sus operaciones ya que está escrito en lenguaje C++.

Para el almacenamiento de la información, utiliza un sistema propio de documento conocido con el nombre BSON, que es una evolución del conocido JSON pero con la peculiaridad de que puede almacenar datos binarios.

En poco tiempo, MongoDB se ha convertido en una de las bases de datos NoSQL favoritas por los desarrolladores.

## Instalar MongoDB Community Edition

Siga estos pasos para instalar MongoDB Community Edition utilizando el administrador de paquetes apt.


### Importar la clave pública utilizada por el sistema de gestión de paquetes.

Desde un terminal, emita el siguiente comando para importar la clave pública GPG MongoDB desde https://www.mongodb.org/static/pgp/server-4.2.asc:

```js
wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -
```
La operación debe responder con un OK.

Sin embargo, si recibe un error que indica que gnupg no está instalado, puede

### Instale gnupg y sus bibliotecas necesarias con el siguiente comando:

```js
sudo apt-get install gnupg
```
### Una vez instalado, vuelva a intentar importar la clave:

```js
wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -
```
### Cree un archivo de lista para MongoDB.

Cree el archivo de lista /etc/apt/sources.list.d/mongodb-org-4.2.list para su versión de Ubuntu.

Haga clic en la pestaña correspondiente a su versión de Ubuntu. Si no está seguro de qué versión de Ubuntu está ejecutando el host, abra una terminal o shell en el host y ejecute lsb_release -dc.

Las siguientes instrucciones son para Ubuntu 18.04 (Bionic). Para Ubuntu 16.04 (Xenial), haga clic en la pestaña correspondiente.

Cree el archivo /etc/apt/sources.list.d/mongodb-org-4.2.list para Ubuntu 18.04 (Bionic):

```js
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list
```
### Vuelva a cargar la base de datos del paquete local.

Emita el siguiente comando para volver a cargar la base de datos del paquete local:



### Instale los paquetes MongoDB.

Puede instalar la última versión estable de MongoDB o una versión específica de MongoDB.

Para instalar la última versión estable, emita lo siguiente

```js
sudo apt-get install -y mongodb-org
```
## Ejecute MongoDB Community Edition

### Consideraciones ulimit
La mayoría de los sistemas operativos tipo Unix limitan los recursos del sistema que puede usar una sesión. Estos límites pueden afectar negativamente la operación de MongoDB. Consulte Configuración de ulimit de UNIX para obtener más información.

### Directorios
Si instaló a través del administrador de paquetes, el directorio de datos / var / lib / mongodb y el directorio de registro / var / log / mongodb se crean durante la instalación.

Por defecto, MongoDB se ejecuta utilizando la cuenta de usuario mongodb. Si cambia el usuario que ejecuta el proceso MongoDB, también debe modificar el permiso para los directorios de datos y registros para dar acceso a este usuario a estos directorios.
### Archivo de configuración
El paquete oficial de MongoDB incluye un archivo de configuración (/etc/mongod.conf). Estas configuraciones (como el directorio de datos y las especificaciones del directorio de registro) entran en vigencia al inicio. Es decir, si cambia el archivo de configuración mientras se ejecuta la instancia de MongoDB, debe reiniciar la instancia para que los cambios surtan efecto.

### Procedimiento

Siga estos pasos para ejecutar MongoDB Community Edition en su sistema. Estas instrucciones asumen que está utilizando el paquete oficial mongodb-org, no el paquete no oficial mongodb proporcionado por Ubuntu, y está utilizando la configuración predeterminada.

Para ejecutar y administrar su proceso mongod, utilizará el sistema de inicialización integrado de su sistema operativo. Las versiones recientes de Linux tienden a usar systemd (que usa el comando systemctl), mientras que las versiones anteriores de Linux tienden a usar System V init (que usa el comando de servicio). Consulte la documentación de su sistema operativo para obtener más información.

Utilice el sistema de inicialización apropiado para su plataforma:

### Inicie MongoDB.

Puede iniciar el proceso mongod emitiendo el siguiente comando:

```js
sudo systemctl start mongod
```
### Comience a usar MongoDB.

Inicie un shell mongo en la misma máquina host que el mongod. Puede ejecutar el shell mongo sin ninguna opción de línea de comandos para conectarse a un mongod que se ejecuta en su host local con el puerto predeterminado 27017:

```js
mongo
```