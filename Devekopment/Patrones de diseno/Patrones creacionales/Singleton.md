#### Singleton
**Singleton** es un patrón de diseño creacional que nos permite asegurarnos de que una clase tenga una única instancia, a la vez que proporciona un punto de acceso global a dicha instancia.

![[Pasted image 20220401121710.png]]

#### Problema

El patrón Singleton resuelve dos problemas al mismo tiempo, vulnerando el _Principio de responsabilidad única_:

1.  **Garantizar que una clase tenga una única instancia**. ¿Por qué querría alguien controlar cuántas instancias tiene una clase? El motivo más habitual es controlar el acceso a algún recurso compartido, por ejemplo, una base de datos o un archivo.
    
    Funciona así: imagina que has creado un objeto y al cabo de un tiempo decides crear otro nuevo. En lugar de recibir un objeto nuevo, obtendrás el que ya habías creado.
    
    Ten en cuenta que este comportamiento es imposible de implementar con un constructor normal, ya que una llamada al constructor siempre **debe** devolver un nuevo objeto por diseño.
	![[Pasted image 20220401121742.png]]
	
2.  **Proporcionar un punto de acceso global a dicha instancia**. ¿Recuerdas esas variables globales que utilizaste (bueno, sí, fui yo) para almacenar objetos esenciales? Aunque son muy útiles, también son poco seguras, ya que cualquier código podría sobrescribir el contenido de esas variables y descomponer la aplicación.
    
    Al igual que una variable global, el patrón Singleton nos permite acceder a un objeto desde cualquier parte del programa. No obstante, también evita que otro código sobreescriba esa instancia.
    
    Este problema tiene otra cara: no queremos que el código que resuelve el primer problema se encuentre disperso por todo el programa. Es mucho más conveniente tenerlo dentro de una clase, sobre todo si el resto del código ya depende de ella.
    

Hoy en día el patrón Singleton se ha popularizado tanto que la gente suele llamar _singleton_ a cualquier patrón, incluso si solo resuelve uno de los problemas antes mencionados.


#### Solucion 

Todas las implementaciones del patrón Singleton tienen estos dos pasos en común:

-   Hacer privado el constructor por defecto para evitar que otros objetos utilicen el operador `new` con la clase Singleton.
-   Crear un método de creación estático que actúe como constructor. Tras bambalinas, este método invoca al constructor privado para crear un objeto y lo guarda en un campo estático. Las siguientes llamadas a este método devuelven el objeto almacenado en caché.

Si tu código tiene acceso a la clase Singleton, podrá invocar su método estático. De esta manera, cada vez que se invoque este método, siempre se devolverá el mismo objeto.

#### Analogia en el mundo real

El gobierno es in ejemplo excelente del patron Singleton. Un pais solo puede tener un gobierno oficial. Independiente de las identidades personales de los individuos que forman el gobierno, el titulo "Gobierno de X" es un punto de acceso global que identifica al grupo de personas a cargo.

#### Estructura

![[Pasted image 20220401122038.png]]

1. La clase **Singleton** declara el metodo estatico obtenerInstancia que devuelve la misma instancia de su propia clase.
	El constructor del Singleton debe ocultarse del codigo cliente. La llamada al metodo obtenerInsdtancia debe ser la unica manera de obtener el objeto de Singleton.