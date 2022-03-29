
#### @SpringBootApplication annotation

Many Spring Boot developers like their apps to use auto-configration, component scan and be able to define extra configuration on their "application class". A single @SpringBootApplication annotation can be used to enable those three features, that is:

 - @EnableAutoConfiguration: enable Spring Boot's auto-configuration mechanism
 - @ComponentScan: enable @Component scan on the package where the application is located.
 - @SpringBootConfiguration: enable registration of extra beans in the context or the import of additional configuration classes. An alternative to Spring's standerd @Configuration that aids configuration detections in your integration tests.

````java
	@SpringBootApplication
	public class MyApplication{
		SpringBootApplication.run(MyApplication.class, args);
	}

````

>@SpringBootApplication also provides aliases to customize the attributes of @EnableAutoConfiguration and @ComponentScan

>None of the features are mandatory and you may choose to replace this single annotation by any of the features that it enables. For instance, you may not want to use component scan or configuration properties scan in your application:
> ````java
	> @SpringBootConfiguration(proxyBeanMethods = false)
	> @EnableAutoConfiguration
	> @Import({ SomeConfiguration.class, AnotherConfiguration.class })
	> public class MyApplication{
		> public static void main (String[] args){
		> SpringApplication.run(MyApplication.class, args);
		> }
	> }
> ````


In this example, MyApplication is just like any other Spring Boot applciation except that @Component- annotated classes and @ConfigurationProperties- annotated classes are not detected automatically and the use-defined beans are imported explicitly (see @Import).

