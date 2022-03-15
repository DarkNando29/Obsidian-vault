# Estructura fundamental

### Block header
- Version: 
	Numero de version de software, si se actualiza el software, se especifica una nueva version
- Previous Block Hash:
	Referencia al hash del bloque previo en la cadena
- Merkle Root:
	Hash de la raiz del merkle tree de las transacciones asociadas a este bloque.
- Timestamp:
	Timestamp actual del bloque en segundos desde 1970-01-01T00:00 UTC
- Difficulty Target:
	La dificultad asociada al algoritmo de proof-of-work para este bloque
- Nonce:
	Contador usado para el algoritmo de proof-of-work.
		
### Identificadores:
- El block hash se calcula al pasar 2 veces el encabezado atraves del algoritmo SHA256.
	
- El block hash identifica un bloque de manera unica.
	
- Block height es la posicion del bloque dentro de la cadena.
	
### Como se unen los bloques:
- Mediante el campo previous bloch hash
	
### Merkle trees
- Estructura de datos usada para resumir y verificar grandes conjuntos de datos
	
- Algoritmo usado por Bitcoin: double-SHA256
	
- Huella digital del conjunto de transacciones dentro del bloque.

#### Como hacer arboles de merkle
Son arboles binarios 

![[Pasted image 20220315155156.png]]

### Red P2P
- Todos los participantes son pares entre si, todos son iguales.
- Resilientes, descentralizada y abierta.
- Bitcoin, Napster, BitTorrent

#### Red de bitcoin
- Conjunto de nodos corriendo el protocolo bitcoin
- Protocolos adicionales usan el p2p de bitcoin y extienden la red a otros nodos corriendo esos protocolos adicionales.
- Extended Bitcoin Network.

##### Tipos de nodos
- Full node:
	- Nodo que valida la cadena completa y sus transacciones.
	- Mantienen un estado actualizado, un conjunto de UTXO.
- Pruning nodes
	- Nodo que descarga y procesa bloques para generar una base de datos para validacion.
	- Desecha bloques antiguos para ahorrar espacio.
- Archive nodes
	- Contiene una copia de toda la historia de la cadena.
	- Valida y consulta transacciones y bloques en cualquier punto del historico.
	- Entregan el historial a nuevos nodos para que se conviertan en full nodes.
- Mining nodes
	- Compiten por crear nuevos bloques
	- Validan transacciones
	- Fundamentales para la seguridad y el consenso de la red
	- Mantienen el mempool de transacciones no confirmadas
	- Mining pools
- Simplified payment verification (SPV)
	- Operan sin almacenar la cadena completa
	- Descargan solo los encabezados
	- Condian en otros nodos para validar bloques y transacciones
	- Profundidad vs Altura
	- Merkle Path
- Otros conceptos
	- Descarga del bloque inicial 
	- Bitcoin core
	- Nodo como servicio.

## Informacion en un nodo
- Estado:
	- Lista de transacciones que no se han gastado.
- Bd bloques:
	- Informacion que tenemos actualmente en el libro mayor actualizado.
- Mempool:
	- Estructura que contiene los mejores candidatos (transacciones) para minar (agregar nuevo bloque).
	- Politicas
		- Ejemplo:
			- Transaccion muy grande o muy pequena.

> El estado actual es uno de los insumos para validar nuevas transacciones
> Con las transacciones que llegan en un nuevo bloque se actualiza el set de UTXO borrando los que se gastaron y agregando los nuevos creados por las transacciones.

![[Pasted image 20220315161659.png]]