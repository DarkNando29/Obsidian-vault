[[Spring Boot Developing]]
## Inversion de control

- Principio que transfiere el control de objetos de un programa a un contenedor o framework
- A diferencia con llevar el flijo de un programa de manera tradicional

![[Pasted image 20220403030535.png]]

``` java

public class Generals {
	public static void main(String[] args){
		List<Integer> lista = Arrays.asList(1,2,3);
		int number = 5;
		for (int value: lista){
			//....
		}
		System.out.println(number);
	}
}

```

Encargarse de toda la inicializacion de la aplicacion.

#### Ventajas de IoC
- Desacomplamiento cuando los objetos cuentan con sus dependencias.
- Se oculta la implementacion de las dependencias, beneficio de segregacion de interfaces.
- Facilita el testing por componentes o mocks de dependencias.
- Mayor modularidad de un programa.

``` java 
	public interface Dependencia {
		void implementation();
	}
	
	public class Objeto implements Dependencia {
		@Override
		public void implementation() {
			//....
		}
	}

	public class Objeto2 implements Dependencia {
		@Override
		public void implementation() {
			//....
		}
	}

```

#### IoC en el contexto de Spring Boot

- Los objetos que son administrados por el contenedor Spring IoC se denominan beans.
- Un bean es un objeto que es instanciado, ensamblado y administrado por un contenedor Spring IoC.

``` java
	@Bean
	public MyBean anyNameMethod(){
		return new myBeanImpl();
	}
``` 

#### Inyeccion de dependencias (DI)
- La inyeccion de dependencias es el proceso con el que los objetos definen sus dependencias.
- Condigo mas limpio y desacomplamiento mas efectivo cuando cada objeto cuenta con su dependencia.

##### Que es?
- Implementacion del princio de inversion de control.
- Definicion de los otros objetos con los que trabajan.
- Clases mas faciles de probar, en particular cuando son interfaces.

##### DI en Spring Boot

``` java
	@Bean
	public MyBean myBean(){
		return new MyBeanImpl();
	}

	public class ClaseNecesitoDependencia {
		private final MyBean dependencia;
		
		@Autowired
		public ClaseNecesitoDependencia(MyBean dependencia){
			this.dependencia = dependencia;
		}
	}
```

