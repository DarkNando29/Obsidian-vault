## Singleton
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
	
#### Pseudocodigo

En este ejemplo, la clase de conexion de la base de datos actua como Singleto. Esta clase no tiene un constructor public, por lo que la unica manera de obetener su objeto es invocando el metodo obtenerInstancia. Este metodo almacena en cache el primer objeto creado y lo devielve en todas las llamadas siguientes.


``` java
// La clase Base de datos define el método `obtenerInstancia`
// que permite a los clientes acceder a la misma instancia de
// una conexión de la base de datos a través del programa.
class Database is
    // El campo para almacenar la instancia singleton debe
    // declararse estático.
    private static field instance: Database

    // El constructor del singleton siempre debe ser privado
    // para evitar llamadas de construcción directas con el
    // operador `new`.
    private constructor Database() is
        // Algún código de inicialización, como la propia
        // conexión al servidor de una base de datos.
        // ...

    // El método estático que controla el acceso a la instancia
    // singleton.
    public static method getInstance() is
        if (Database.instance == null) then
            acquireThreadLock() and then
                // Garantiza que la instancia aún no se ha
                // inicializado por otro hilo mientras ésta ha
                // estado esperando el desbloqueo.
                if (Database.instance == null) then
                    Database.instance = new Database()
        return Database.instance

    // Por último, cualquier singleton debe definir cierta
    // lógica de negocio que pueda ejecutarse en su instancia.
    public method query(sql) is
        // Por ejemplo, todas las consultas a la base de datos
        // de una aplicación pasan por este método. Por lo
        // tanto, aquí puedes colocar lógica de regularización
        // (throttling) o de envío a la memoria caché.
        // ...

class Application is
    method main() is
        Database foo = Database.getInstance()
        foo.query("SELECT ...")
        // ...
        Database bar = Database.getInstance()
        bar.query("SELECT ...")
        // La variable `bar` contendrá el mismo objeto que la
        // variable `foo`.
```

#### Aplicabilidad

**Utiliza el patrón Singleton cuando una clase de tu programa tan solo deba tener una instancia disponible para todos los clientes; por ejemplo, un único objeto de base de datos compartido por distintas partes del programa.**

**Utiliza el patrón Singleton cuando necesites un control más estricto de las variables globales.**

> El patron Singleton deshabilita el resto de las maneras de crear objetos de una clase, excepto el metodo especial de creacion. Este metodo crea un nuevo objeto, o bien devuelve uno existente si ya a sido creado.

> Al contrario que las variables globales, el patron Singleton garantiza que haya una unica instancia de una clase, A excepcion de la propia clase Singleton, nada puede sustituir la instancia en cache.
> Ten en cuenta que siempre podras ajustar esta limitacion y permitir la creacion de cierto numero de instancia SDingleton. La unica parte del codigo que requiere cambios es el cuerpo del metodo _getInstance_.

#### Como implementarlo?

1. Anade un campo estatico privado a la clase para almacenar la instancia Singleton.
2. Declara un metodo de creacion estatico publico para obtener la instancia Singleton.
3. Implementa una inicializacion diferida dentro del metodo estatico. Debe crear un nuevo objeto en su primera llamada y colocarlo dentro del campo estatico. El metodo debera devolver siempre esa instancia en todas las llamadas siguientes.
4. Declara el constructor de clase como privado. El metodo estatico de la clase seguira siendo capaz de invocar al constructor, pero no a los otros objetos.
5. Repasa el codigo cliente y sustituye todoas las llamadas directas al constructor de la instancia Singleton por llamdas a su metodo de creacion estatico.

#### Pros y contras

|Definicion |Pros|Contras|
|----|----|-----|
| Puedes tener la certeza de que una clase tiene una única instancia.| [ x ] | [  ] | 
| Obtienes un punto de acceso global a dicha instancia..| [ x ] | [  ] | 
| El objeto Singleton solo se inicializa cuando se requiere por primera vez..| [ x ] | [  ] | 
| Vulnera el _Principio de responsabilidad única_. El patrón resuelve dos problemas al mismo tiempo..| [  ] | [ x ] | 
| El patrón Singleton puede enmascarar un mal diseño, por ejemplo, cuando los componentes del programa saben demasiado los unos sobre los otros..| [  ] | [ x ] | 
| El patrón requiere de un tratamiento especial en un entorno con múltiples hilos de ejecución, para que varios hilos no creen un objeto Singleton varias veces.| [  ] | [ x ] | 
| Puede resultar complicado realizar la prueba unitaria del código cliente del Singleton porque muchos _frameworks_ de prueba dependen de la herencia a la hora de crear objetos simulados (mock objects). Debido a que la clase Singleton es privada y en la mayoría de los lenguajes resulta imposible sobrescribir métodos estáticos, tendrás que pensar en una manera original de simular el Singleton. O, simplemente, no escribas las pruebas. O no utilices el patrón Singleton..| [  ] | [ x ] | 