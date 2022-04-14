## Linked List

Es parte de Collection Framework presente en java.util.package. Esta clase es una implementacion de la estructura de datos LinkedList la cual es una estructura de datos lineal donde los elementos no son almacenados en lugares continuos y cada elmento es un objeto separado con una parte de datos y de direccion. 

- Los elementos estan enlazados usando punteros y direcciones.
- Cada elemento es conocido como nodo. 
- Debido a la dinamica y facilidad de insercion y eliminacion, son preferibles a los arreglos.
- Tambien tiene algunas desventajas, como que no se puede acceder directamente a los nodos, sino que debemos comenzar desde la cabeza y seguir el enlace para llegar al nodo al que deseamos acceder.

Desde que una linkedList actua como una array dinamico y no tenemos que especificar el tamano mientras lo creamos, el tamano de la lista aumenta o disminuye cuando dinamicamente agregamos o removemos objetos dentro de el.Y tambien, los elementos no son almacenados en bonitos lugares continuos. Por esto, no es necesario incrementar el tamano.Internamente, el LinkedList is implementado usando [doubly linked list data structure](https://www.geeksforgeeks.org/doubly-linked-list/). La mayor diferencia entre un LinkedList normal y un doble LinkedList es eso, una doble lista de enlaces conteniendo un puntero extra, normalmente llamado puntero anterior, juntos con el siguiente puntero y datos que estan en una sola LinkedList.

#### Constructores en un LinkedList
En orden para crear una LinkedList, necesitamos crear un objeto de clase LinkedList. La clase LinkedList consiste de varios constructores que habilitan la posibilidad de crear una lista. Los siguientes son constructores que estan habilitados en esta clase. 

**1. LinkedList():** Este constructor es usado para crear un LinkedList vacia. Si deseamos crear una LinkedList vacia con el nombre ll entonces usamos lo siguiente: 

LinkedList ll = new LinkedList();  

**2. LinkedList(Collection C):** Este constructor es usado para crear una lista ordenada que contiene todos los elementos de una coleccion especifica, como retorno por una coleccion de iteracion. Si deseamos crear una LinkedList con el nombre ll entonces lo creamos de la siguiente manera:

LinkedList ll = new LinkedList(C);
