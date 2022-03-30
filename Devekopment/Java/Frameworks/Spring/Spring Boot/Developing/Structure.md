[[Spring Boot Developing]]

Spring Boot does not require any specific code layout to work. However, there are some best practices that help.

#### Using the "default" package.

When a class does not include a package declaration, it is considered to be in the "default package". The use of the "default package" is fenerally discouraged and should be avoided. It can cause particular problems for Spring Boot applications that use the @ComponentScan, @ConfigurationPropertiesScan, @EntityScan or @SpringBootApplication annotations, since every class from every jar is read.

> Recommended that follow Java's recommended package naming conventions and use a reversed domain name (for example, com.example.project).

#### Location the main class

The use of @SpringBootApplication annotations it should be located in the root package above other classes.

> com
> 	+-	example
>		+- myapplication
>			+- MyApplication.java
>			|
>			+- customer
>			|	+- Customer.java
>			|	+- CustomerController.java
>			| 	+- CustomerService.java
>			|	+- CustomerRepository.java
>			+- order
>			|	+- Order.java
>			|	+- OrderController.java
>			| 	+- OrderService.java
>			|	+- OrderRepository.java
			
The MyApplication.java file would declare the main method, along with the basic @SpringBootApplication, as follows:

> @SpringBootApplication
	public class MyApplication {
		public static void main(String[] args){
			SpringApplication.run(MyApplication.class, args);
		}
	}
	
	
