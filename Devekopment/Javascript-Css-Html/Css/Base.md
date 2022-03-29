#### Bases
Hojas de estilo en cascada

- Lenguaje que le da vida a tu "esqueleto"
	- Colores
	- Tamanos
	- Ubicaciones
	- Etc

#### Anatomia del CSS
- Selector: h1
- Propiedad: color
- Valor: pink

	```` css
	h1 {
	color: pink;
	}
	````

#### Tipos de selectores(basicos o combinados)
##### Basicos
| Tipo | Ejemplo |
|-|-|
| De tipo | div|
| De clase | .elemento|
| De id | #id-del-elemento |
| De atributo|a[href=""] |
| Universal | * |

##### Combinadores
| Tipo | Ejemplo |
|-|-|
| Descendientes| div p|
| Hijo directo | div > p|
| Elemento adyacente  | div + p |
| General de Hermanos | div ~ p |

##### Pseudoclases- Pseudoelementos

| Pseudoclases | Pseudoelementos |
|-|-|
| :active| ::after |
| :focus | ::before |
| :hover | ::first-letter |
| :nth-child(n) | ::placeholder |

##### Cascada y especificidad
- Order y reglas
	- !important
	- estilos en linea
	- id
	- clases, atributos y pseudoclases
	- elementos y pseudoelementos
	- selector universal

##### Tipos de display mas usados

- Block
- inline
- inline-block
- flex
	- flex-direction
	- justify-content
	- align-items
- grid

##### Modelo de caja
- Se colapsan si son tipo bock si es tipo grid o flex no lo hacen.
- Margin  (t, r, b, l) parte externa
	- Border  (t, r, b, l)
		- Padding  (t, r, b, l) parte interna
			- Content (height y width)
##### Posicionamiento (position)
1. Relative (se acerca pero no se pega al contenedor) 
2. Absolute (se adhiere al contenedor)
3. Fixed (estatico)
4. Sticky (pegarse)
5. Static ()
6. Initial
7. Inherital

##### Apilamiento
Una vez asignado un z-index, se forman capas sobre capas en el layout.