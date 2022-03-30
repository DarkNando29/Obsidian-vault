[[Patrones de diseno Creacionales]]

**Abstract Factory** es un patrón de diseño creacional que resuelve el problema de crear familias enteras de productos sin especificar sus clases concretas.

>El patrón Abstract Factory define una interfaz para crear todos los productos, pero deja la propia creación de productos para las clases de fábrica concretas. Cada tipo de fábrica se corresponde con cierta variedad de producto.

>El código cliente invoca los métodos de creación de un objeto de fábrica en lugar de crear los productos directamente con una llamada al constructor (operador `new`). Como una fábrica se corresponde con una única variante de producto, todos sus productos serán compatibles.

>El código cliente trabaja con fábricas y productos únicamente a través de sus interfaces abstractas. Esto permite al mismo código cliente trabajar con productos diferentes. Simplemente, creas una nueva clase fábrica concreta y la pasas al código cliente.


#### Problema
Imagina que estas creando un simulador de tienda de muebles. Tu codigo esta compuesto por clases que representan lo siguiente:

1. Una familia de productos relacionados, digamos: Silla + Sofa + Mesilla.
2. Algunas variantes de esta familia. Por ejemplo, los productos Silla + Sofa + Mesilla estan disponibles en estas variantes: Moderna + Victoriana + ArtDeco.

Necesitamos una forma de crear objetos individuales de mobiliario para que combinen con otros objetos de la misma. Lo clientes se enfadan bastantes cuando reciben muebles que no cambinan.

Ademas, no queremos cambiar el codigo existentes al anadir al programa nuevos productos o familias de productos. Los comerciantes de muevles actualizan sus catalogos muy a menudo, y debemos evitar tener que cambiar el codigo principal cada vez que esto ocurra.

#### Solucion
Lo primero que sugiere el patron Abstract Factory es que declaremos de forma explicita interfaces para cada producto diferente de la familia de productos (por ejemplo, silla, sofa o mesilla). Despues podemos hacer que todas las variantes de los productos sigan esas interfaces. Por ejemplo, todas las variantes de sillas pueden implementar la interfaz silla, asi como todas las variantes de mesilla pueden implementar la interfaz Mesilla, y asi sucesivamente.

![[Pasted image 20220329235603.png]]

El siguiente paso consiste en declarar el Abstract Factoy: una interfaz con una lista de metodos de creacion para todos los productos que son parte de la familia de productos ( por ejemplo, crearSilla, crearSofa, crearMesilla).
Estos metodos deben devolver productos abstractos representados por las interfaces que extrajumos previamente: Silla, Sofa, Mesilla, etc.

![[Pasted image 20220329235825.png]]

Ahora bien, que hay de las variantes de los productos? Para cada variante de una familia de productos, creamos una clase de fabrica independiente basada en la interfaz fabricaAbstracta. Una fabrica es una clase que devuelve productos de un tipo particular. Por ejemplo, la FabricaMueblesModernos solo puede crear objetos de SillaModerna, SodaModerno y MesillaModerna.

El codigo cliente tiene que functionar con fabricas y productos a traves de sus respectivas interfaces abstractas. Esto nos permite cambiar el tipo de fabrica que pasamos al codigo cliente, asi como la variante del producto que recibe el codigo cliente, sin descomponer el propio codigo cliente.

Digamos que el cliente quiere una fabrica para producir una silla. El cliente no tiene que conocer la clase de la fabrica y tampoco importa el tipo de silla que obtiene. Ya sea un modelo modenos o una silla de estilo victoriano, el cliente debe tratar a todas las sillas del mismo modo, utilizando una interfaz abstracta Silla. Con este sistema, lo unico que sabe el cliente sobre la silla es que implementa de algun modo el metodo sentarse. Ademas, sea cual sea la variante de la silla devuelta, siempre combinara con el tipo de sofa o mesilla producida por el mismo objeto de fabrica.

Queda otro punto a aclarar: si el cliente solo esta expuesto a las interfaces abstractas, como se crean los objetos de fabrica? Normalmente, la aplicacion crea un objeto de favrica concreto en la etapa de inicializacion. Justo antes, la aplicacion debe seleccionar el tipo de fabrica, dependiento de la configuracion o de los ajustes del enterno.

#### Estructura
![[Pasted image 20220330000903.png]]

1. Los productos abstractos declaran interfaces para un grupo de productos diferentes pero relacionados que forman una familia de productos.
2. Los Productos Concretos son implementaciones distintas de productos asbtractos agrupados por variantes. Cada producto abstracto (silla/sofa) debe implementarse en todas las variantes dadas (victoriano/moderno).
3. La interfaz fabrica Abstracta declara un grupo de metodos para crear cada uno de los productos abstractos.
4. Las fabricas concretas implementan metodos de creacion de la fabrica abstracta. Cada fabrica concreta se corresponden con una variante especifica de los productos y crea tan solo dichas variantes de los productos.
5. Aun que las fabricas concretas instancian productos concretos, las firmas de sus metodos de creacion deben devolver los productos abstractos correspondientes. De este modo, el codigo cliente que utiliza una fabrica no se acopla a la variante especifica del producto que obtiene de una fabrica. El **Cliente** puede funcionar con cualquier variante fabrica/producto concreta, siempre y cuando se comunique con sus objetos a traves de interfaces abstractas.

#### Pseudocodigo python
````python
// La interfaz fábrica abstracta declara un grupo de métodos que
// devuelven distintos productos abstractos. Estos productos se
// denominan familia y están relacionados por un tema o concepto
// de alto nivel. Normalmente, los productos de una familia
// pueden colaborar entre sí. Una familia de productos puede
// tener muchas variantes, pero los productos de una variante
// son incompatibles con los productos de otra.
interface GUIFactory is
    method createButton():Button
    method createCheckbox():Checkbox

// Las fábricas concretas producen una familia de productos que
// pertenecen a una única variante. La fábrica garantiza que los
// productos resultantes sean compatibles. Las firmas de los
// métodos de las fábricas concretas devuelven un producto
// abstracto mientras que dentro del método se instancia un
// producto concreto.
class WinFactory implements GUIFactory is
    method createButton():Button is
        return new WinButton()
    method createCheckbox():Checkbox is
        return new WinCheckbox()

// Cada fábrica concreta tiene una variante de producto
// correspondiente.
class MacFactory implements GUIFactory is
    method createButton():Button is
        return new MacButton()
    method createCheckbox():Checkbox is
        return new MacCheckbox()

// Cada producto individual de una familia de productos debe
// tener una interfaz base. Todas las variantes del producto
// deben implementar esta interfaz.
interface Button is
    method paint()

// Los productos concretos son creados por las fábricas
// concretas correspondientes.
class WinButton implements Button is
    method paint() is
        // Representa un botón en estilo Windows.

class MacButton implements Button is
    method paint() is
        // Representa un botón en estilo macOS.

// Aquí está la interfaz base de otro producto. Todos los
// productos pueden interactuar entre sí, pero sólo entre
// productos de la misma variante concreta es posible una
// interacción adecuada.
interface Checkbox is
    method paint()

class WinCheckbox implements Checkbox is
    method paint() is
        // Representa una casilla en estilo Windows.

class MacCheckbox implements Checkbox is
    method paint() is
        // Representa una casilla en estilo macOS.

// El código cliente funciona con fábricas y productos
// únicamente a través de tipos abstractos: GUIFactory, Button y
// Checkbox. Esto te permite pasar cualquier subclase fábrica o
// producto al código cliente sin descomponerlo.
class Application is
    private field factory: GUIFactory
    private field button: Button
    constructor Application(factory: GUIFactory) is
        this.factory = factory
    method createUI() is
        this.button = factory.createButton()
    method paint() is
        button.paint()

// La aplicación elige el tipo de fábrica dependiendo de la
// configuración actual o de los ajustes del entorno y la crea
// durante el tiempo de ejecución (normalmente en la etapa de
// inicialización).
class ApplicationConfigurator is
    method main() is
        config = readApplicationConfigFile()

        if (config.OS == "Windows") then
            factory = new WinFactory()
        else if (config.OS == "Mac") then
            factory = new MacFactory()
        else
            throw new Exception("Error! Unknown operating system.")

        Application app = new Application(factory)
````

#### Aplicacabilidad

**Utiliza el patron Abstract Factory cuando tu codigo deba funcionar con varias familias de productos relacionados, pero no desees que dependa de las clases concretas de esos productos, ya que puede ser que no los conozcas de antemano o sencillamente quiereas permitir una futura extensibilidad.**