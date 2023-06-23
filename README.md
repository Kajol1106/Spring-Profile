### Spring-Profile :
#### Example : 
1. From one interface we implementd more than one class and making the component then we have to set the @Primary attribute for one class otherwise it will throw the error
```
Animal Interface :
==================
public interface Animal {
	public void makeSound();
}

Dog Class :
===========
import org.springframework.context.annotation.Profile;
import org.springframework.stereotype.Component;
@Component
@Profile("dog")
public class Dog implements Animal{
	@Override
	public void makeSound() {
		System.out.println("Bhow...");
	}
}

Cat Class :
===========
import org.springframework.context.annotation.Primary;
import org.springframework.context.annotation.Profile;
import org.springframework.stereotype.Component;
@Component
@Profile("cat")
@Primary
public class Cat implements Animal{
	@Override
	public void makeSound() {
		System.out.println("Meew....");
	}
}

application.properties :
========================
spring.profiles.active=cat

Main Method :
==============
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import com.cf.seleniumexpress.Animal;
@SpringBootApplication
public class SpringProfilesDemoApplication implements CommandLineRunner{
	@Autowired
	private Animal animal;
	
	public static void main(String[] args) {
		SpringApplication.run(SpringProfilesDemoApplication.class, args);
	}

	//for override this method we have need to implement CommandLineRunner
	@Override
	public void run(String... args) throws Exception {
		System.out.println(animal);
		animal.makeSound();
	}
}

```

2. We can define method also as a bean :
3. 
