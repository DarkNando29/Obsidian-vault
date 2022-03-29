#### Spring Beans and Dependency Injection

Your are free to use any of the standard Spring Framework techniques to define your beans and their injected dependencies. We generally recommend using constructor injection to wire up dependencies and @ComponentScan to find beans.

If you structure your code as suggested above (locating your application class in a top package), you can add @ComponentScan without any arguments or use the @SpringBootApplication annotation which implicity includes it. All of your application components (@Component, @Service, @Repository, @Controller, and others) are automatically registered as Spring Beans.

The following example shows a @Service Bean that uses constructor injection to obtain a required RiskAssesor bean:

````java 
	@Service
	public class MyAccountService implements AccountService {
		private final RiskAssesor riskAssesor;
		
		public MyAccountService(RiskAssesor riskAssesor){
			this.riskAssesor = riskAssesor;
		}
		
		//..
	}
````
	
If a bean has more than one constructor, you will need to mark the one you want Spring to use with @Autowired:

````java 
	
	@Service
	public class MyAccountService implements AccountService {
		private final RiskAssesor riskAssesor;
		private final PrintStream out;
		
		@Autowired
		public MyAccountService(RiskAssesor, riskAssesor){
			this.riskAssesor = riskAssesor;
			this.out = System.out;
		}
		
		public MyAccountService(RiskAssesor riskAssesor, PrintStream out){
			this.riskAssesor = riskAssesor;
			this.out = out;
		}
		
		//	...
	}

````

>Tip: Notice how using constructor injestion lets the riskAssesor field be marked as final, indicvcation that it cannot be subsequently changed.

