[[Spring Boot Developing]]

Spring Boot favors Java-based configuration. Although it is possible to use SpringAplication with XML sources, we generally recommend that your primary soruce be a single @Configuration class. Usually the class that defines the main method is a good candidate as the primary @Configuration.

> Many Spring configuration examples have been published on the internet that use XML configuration. If possible, always try to use the equivalent Java-based configuration. Searching for Enable annotations can be good stating point.

#### Importing Additional Configuration Classes
You need not to pull all your @Configuration into a single class. The @Import annotation can be used to import additional configuration classes. Alternatively, you can use @ComponentScan to automatically pick up all Spring components, including @Configuration classes.

#### Importing XML configuration

If you absolutely must use XML based configuration, we recommend that you still start with a @Configuration class. You can then use an @ImportResource annotation to load XML configuration files.


