## addAll

#### Definition
Este metodo inserta todos los elementos en la coleccion especifica dentro de la lista, empezando en una posicion especifica.

#### Code
``` java
// Java code to illustrate boolean addAll()
import java.util.*;
import java.util.LinkedList;
import java.util.ArrayList;

public class LinkedListDemo {
public static void main(String args[]) {

	// Creating an empty LinkedList
	LinkedList<String> list = new LinkedList<String>();

	// Use add() method to add elements in the list
	list.add("Geeks");
	list.add("for");
	list.add("Geeks");
	list.add("10");
	list.add("20");
		
	// Creating a Collection
	Collection<String> collect = new ArrayList<String>();
	collect.add("A");
	collect.add("Computer");
	collect.add("Portal");
	collect.add("for");
	collect.add("Geeks");

	// Displaying the list
	System.out.println("The LinkedList is: " + list);
			
	// Appending the collection to the list
	list.addAll(1, collect);

	// Clearing the list using clear() and displaying
	System.out.println("The new linked list is: " + list);

}
}
``` 

#### Ways

> addAll(int index, Collection<E> e)
> addAll(Collection<E> e)
	

