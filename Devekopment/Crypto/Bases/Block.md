# Estructura fundamental

### Block header
	-Version: 
		Numero de version de software, si se actualiza el software, se especifica una nueva version
	-Previous Block Hash:
		Referencia al hash del bloque previo en la cadena
	-Merkle Root:
		Hash de la raiz del merkle tree de las transacciones asociadas a este bloque.
	-Timestamp:
		Timestamp actual del bloque en segundos desde 1970-01-01T00:00 UTC
	-Difficulty Target:
		La dificultad asociada al algoritmo de proof-of-work para este bloque
	-Nonce:
		Contador usado para el algoritmo de proof-of-work.
		
### Identificadores: