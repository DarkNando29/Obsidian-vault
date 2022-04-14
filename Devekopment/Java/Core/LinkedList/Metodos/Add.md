Como todos sabemos que la clase LinkedList contiene varios métodos, aquí discutiremos e implementaremos el método add() para comprender mejor cómo se agregan los elementos en una LinkedList. 

Para eso, consulte el siguiente diagrama de flujo para obtener una mejor comprensión de cualquier método. Tenga en cuenta que es muy importante revisar los diagramas de flujo en la programación. Aquí surgen dos casos: la adición predeterminada de elementos y la adición personalizada de elementos. Aquí los cubriremos a ambos de la siguiente manera:

![[Pasted image 20220403004957.png]]

``` java 
// Java Program to Illustrate add() Method
// of LinkedList class
// Where we are Adding at Last of List

// Importing required classes
import java.io.*;
import java.util.LinkedList;

// Main class
public class GFG {

	// Main driver method
	public static void main(String args[])
	{

		// Creating an empty LinkedList
		LinkedList list = new LinkedList();

		// Adding elements in the list
		// using add() method
		list.add("Geeks");
		list.add("for");
		list.add("Geeks");
		list.add("10");
		list.add("20");
		list.add(10, "Element");
		list.add(15, "Fire");

		// Printing the elements of current LinkedList
		System.out.println("The list is:" + list);

		// Adding new elements to the end
		// Note: Default addition happens from last
		list.add("Last");
		list.add("Element");

		// Printing elements of updated LinkedList
		System.out.println("The new List is:" + list);
	}
}
``` 
