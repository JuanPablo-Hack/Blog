---
path: "/BlockChain/"
category: "Go"
tags: ["tag"]
title: "Blockchain con Go"
date: "2020-03-21T18:30:00.000Z"
summary: "En esta ocasion utilizaremos el algoritmo de Blockchain para guardar unos datos..."
images: ["images/bc.jpeg"]
---

> "Blockchain es un algoritmo super poderoso y seguro, es el futuro de la estructura de datos." 

>   Figueroa 2020

Una cadena de bloques,​ conocida en inglés como blockchain,​ es una estructura de datos en la que la información contenida se agrupa en conjuntos (bloques) a los que se les añade metainformaciones relativas a otro bloque de la cadena anterior en una línea temporal, de manera que gracias a técnicas criptográficas, la información contenida en un bloque solo puede ser repudiada o editada modificando todos los bloques posteriores. Esta propiedad permite su aplicación en un entorno distribuido de manera que la estructura de datos blockchain puede ejercer de base de datos pública no relacional que contenga un histórico irrefutable de información.​En la práctica ha permitido, gracias a la criptografía asimétrica y las funciones de resumen o hash, la implementación de un registro contable (ledger) distribuido que permite soportar y garantizar la seguridad de dinero digital.​ Siguiendo un protocolo apropiado para todas las operaciones efectuadas sobre la blockchain, es posible alcanzar un consenso sobre la integridad de sus datos por parte de todos los participantes de la red sin necesidad de recurrir a una entidad de confianza que centralice la información. Por ello se considera una tecnología en la que la "verdad" (estado confiable del sistema) es construida, alcanzada y fortalecida por los propios miembros; incluso en un entorno en el que exista una minoría de nodos en la red con comportamiento malicioso (nodos sybil) dado que, en teoría, para comprometer los datos, un atacante requeriría de una mayor potencia de cómputo y presencia en la red que el resultante de la suma de todos los restantes nodos combinados. 

Por las razones anteriores, la tecnología blockchain es especialmente adecuada para escenarios en los que se requiera almacenar de forma creciente datos ordenados en el tiempo, sin posibilidad de modificación ni revisión y cuya confianza pretenda ser distribuida en lugar de residir en una entidad certificadora.

En este tutorial vamos a hacer nuestro propio algoritmo de blockchain, con el lenguaje de programacion de Go, vamos a comenzar con crear nuestro directorio:

```js
mkdir blockchain-go
```
Como siempre vamos a crear nuestro archivo .go donde vamos a ejecutar y crear nuestro propio algoritmo de blockchain, una vez creado nuestro archivo comenzamos a desarrollar, primero vamos a definir la estructura de nuestro bloque, sabemos que el bloque tiene datos, el hash del bloque anterior, el hash del bloque actual, sabiendo esto declaramos una estructura de la siguiente manera:

```js
//Creamos la estructura del bloque
type Block struct {
	//Ingresamos la fecha
	Timestamp int64
	//Ingresamos los datos
	Data []byte
	//Obtenemos el hash del bloque anterior
	PrevBlockHash []byte
	//Declaramos el hash del bloque
	Hash []byte
	//Dificultad del bloque
	Nonce int
}
```
Ahora vamos a crear la funcion de la creacion de un nuevo bloque:
```js
//Creamos la estructura del bloque
type Block struct {
	//Ingresamos la fecha
	Timestamp int64
	//Ingresamos los datos
	Data []byte
	//Obtenemos el hash del bloque anterior
	PrevBlockHash []byte
	//Declaramos el hash del bloque
	Hash []byte
	//Dificultad del bloque
	Nonce int
}
```
Ahora declaramos la estructura de la cadena de bloques, declarando un arreglo con un puntero:

```js
//Declaramos la estructura de la cadena de bloques
type Blockchain struct {
	//La declaramos como un arreglo con un puntero
	blocks []*Block
}
```
Despues creamos la funcion para poder agregar el bloque a la cadena:
```js
//Creamos la funcion de crear bloque
func (bc *Blockchain) AddBlock(data string) {
	//Revisamos el valor del bloque anterior
	prevBlock := bc.blocks[len(bc.blocks)-1]
	//Enviamos los datos y mandamos a llamar la funcion de crear bloque
	newBlock := NewBlock(data, prevBlock.Hash)
	//Agreamos el bloque al arreglo
	bc.blocks = append(bc.blocks, newBlock)
}
```
Tenemos que declarar un bloque Genesis por lo que es el bloque donde va a inicias nuestra cadena:
```js
//Funcion para agregar el bloque genesis
func NewGenesisBlock() *Block {
	return NewBlock("Genesis Block", []byte{})
}
```
Tambien tenemos que declararle desde donde va a comenzar a agregar bloques:
```js
//Aqui comenzamos con la creacion de la cadena de bloques
func NewBlockchain() *Blockchain {
	return &Blockchain{[]*Block{NewGenesisBlock()}}
}
```
Ahora tenemos que seguir el algoritmo de la prueba de trabajo para agregar una dificultad para agregar un bloque dentro de la cadena:
```js
//Agregamos la dificultad para la creacion del hash
const targetBits = 24

//Declaramos el limite
var (
	maxNonce = math.MaxInt64
)

//Hacemos una validacion del trabajo
type ProofOfWork struct {
	//Apuntamos hacia el bloque
	block *Block
	//Declaramos el arranque
	target *big.Int
}

//Hacemos una nueva validacion del trabajo
func NewProofOfWork(b *Block) *ProofOfWork {
	target := big.NewInt(1)
	target.Lsh(target, uint(256-targetBits))

	pow := &ProofOfWork{b, target}

	return pow
}

//Funcion para convertir un entero en formato hexadecimal
func IntToHex(num int64) []byte {
	buff := new(bytes.Buffer)
	err := binary.Write(buff, binary.BigEndian, num)
	if err != nil {
		log.Panic(err)
	}

	return buff.Bytes()
}

//Funcion de la validacion del trabajo
func (pow *ProofOfWork) prepareData(nonce int) []byte {
	data := bytes.Join(
		[][]byte{
			pow.block.PrevBlockHash,
			pow.block.Data,
			IntToHex(pow.block.Timestamp),
			IntToHex(int64(targetBits)),
			IntToHex(int64(nonce)),
		},
		[]byte{},
	)

	return data
}

//Algoritmo de prueba de trabajo
func (pow *ProofOfWork) Run() (int, []byte) {
	var hashInt big.Int
	var hash [32]byte
	nonce := 0

	fmt.Printf("Minando el contenido del bloque \"%s\"\n", pow.block.Data)
	for nonce < maxNonce {
		data := pow.prepareData(nonce)
		hash = sha256.Sum256(data)
		fmt.Printf("\r%x", hash)
		hashInt.SetBytes(hash[:])

		if hashInt.Cmp(pow.target) == -1 {
			break
		} else {
			nonce++
		}
	}
	fmt.Print("\n\n")

	return nonce, hash[:]
}
```
Por ultimo vamos a mandar llamar a todas nuestras funciones dentro de nuestro programa principal, que seria nuestra funcion main, la cual nos va a quedar de la siguiente manera:
```js
func main() {
	bc := NewBlockchain()

	bc.AddBlock("Juan Pablo de Jesus Figueroa Jaramillo")
	bc.AddBlock("Karen Valeria Ramirez Perez")

	for _, block := range bc.blocks {
		fmt.Printf("Prev. hash: %x\n", block.PrevBlockHash)
		fmt.Printf("Data: %s\n", block.Data)
		fmt.Printf("Hash: %x\n", block.Hash)
		fmt.Println()
	}
}
```
Una vez terminado esto vamos a ejecutar nuestro algoritmo de blockchain para ver que es lo que resulta, como siempre para poder ejecutar un script de Go hacemos lo siguiente:

```js
go run main.go
```
Y listo ya tenemos nuestro algoritmo hecho, con esto podemos iniciar varios proyecto como la elaboracion de una criptomoneda o etc...