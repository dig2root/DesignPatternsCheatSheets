# Factory

Factory design pattern is used to instantiate objects that type is not pre-defined. They are dynamically created depending on parameters specified to the factory.

## UML Class Diagram

![Factory](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/dig2root/DesignPatternsCheatSheets/main/PlantUML/Factory.plantuml "The Factory")

## Code Samples

### Java

```Java
package gof.creational.factory;

public class ProductFactory {

    public Product createProduct(String type) {
        if (type.equals("A")) {
            return new ProductA();
        } else if (type.equals("B")) {
            return new ProductB();
        } else {
            return null;
        }
    }
}

public abstract class Product {
    public abstract void myType();
}

public class ProductA extends Product {
    @Override
    public void myType() {
        System.out.println("I am Product A");
    }
}

public class ProductB extends Product {
    @Override
    public void myType() {
        System.out.println("I am Product B");
    }
}

public class Client {

    public static void main(String[] args) {
        ProductFactory factory = new ProductFactory();
        Product productA = factory.createProduct("A");
        Product productB = factory.createProduct("B");
        productA.myType();
        productB.myType();
    }
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Fabrique](https://fr.wikibooks.org/wiki/Patrons_de_conception/Fabrique)