[[Spring Boot Developing]]

#### Auto-configuration

Spring Boot auto-configration attempsts to automatically configure your Soring application based on the jar dependencies that you have added. For example, if HSQLB is on your classpath, and you have not manually configured any databse connections beans, then Spring Boot auto-configures an in-memory database.

You need to opt-in to autoconfiguration adding the @EnableAutoConfiguration or @SpringBootApplication annotations to one of your @Configuration classes.

> You should only ever add one @SpringBootApplication or @EnableAutoConfiguration annotation. We generally recommend that you add one or the other to your primary @Configuration class only.

#### Gradually Replacing Auto-configuration
Auto-configuration is non-invasive. At any point, you can start to define your own configuration to replace specific parts od the auto-configuration. For example, if you add your own DataSource bean, the default embedded database support backs away.

If you need to find out what auto-configuration is currently being applied, and why start your application with the --debug switch. Doing so enables debug logs for a selection of core loggers and logs a conditions report to the console.

#### Disabling Specific Auto-configuration Classes
If you find that specific auto-configuration classes that you do not want are being applied, you can use the exclude attribute of @SpringBootApplication to disable them, as shown in the following example:

> @SpringBootApplication(exclude= {	DataSoruceAutoConfiguration.class	}	)
	public class MyApplication {
	
	}
	
If the class is not on the classpath, you can use the excludeName attribute of the annotation and specifu the fully qualified name instead. If you prefer to use @EnableAutoConfiguration rather than @SpringBootApplication, exclude and excludeName are alse available. Finally, you can also control the list of auto-configuration classes to exclude by using the spring.autoconfigure.exclude property.

> You can define exclusions both at the annoptation level and by using the property.

>Even though auto-configuration classes are public, the only aspect of the class that is considered public API is the name of the class which can be used for disabling the auto-configuration. The actual contents of those classes, such as nested configuration classes or bean methods are for internel use only and we do not recommend using those directly.


