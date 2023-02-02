# Abstract factory

The Abstract Factory Design Pattern is a creational design pattern that provides an interface for creating families of related or dependent objects without specifying their concrete classes.

The abstract factory allows you to use objects that are suited to your needs, and to switch between them as needed without modifying the client code.

This pattern is useful when you need to create a collection of objects that belong to a certain class hierarchy, but you do not want to expose the concrete classes to the client code.

## UML Class Diagram

![Abstract factory](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/dig2root/DesignPatternsCheatSheets/main/PlantUML/AbstractFactory.puml? "The Abstract Factory")

## Code Samples

### Java

```Java
package gof.creational.abstractFactory;

public interface AbstractFactory {
    public ProductA createProductA();
    public ProductB createProductB();
}

public class ConcreteFactory1 implements AbstractFactory {
    public ProductA createProductA() {
        return new ProductA1();
    }
    public ProductB createProductB() {
        return new ProductB1();
    }
}

public class ConcreteFactory2 implements AbstractFactory {
    public ProductA createProductA() {
        return new ProductA2();
    }
    public ProductB createProductB() {
        return new ProductB2();
    }
}

public interface ProductA {
    public void methodA();
}

public interface ProductB {
    public void methodB();
}

public class ProductA1 implements ProductA {
    public void methodA() {
        System.out.println("ProductA1.methodA()");
    }
}

public class ProductA2 implements ProductA {
    public void methodA() {
        System.out.println("ProductA2.methodA()");
    }
}

public class ProductB1 implements ProductB {
    public void methodB() {
        System.out.println("ProductB1.methodB()");
    }
}

public class ProductB2 implements ProductB {
    public void methodB() {
        System.out.println("ProductB2.methodB()");
    }
}

public class Client {
    public static void main(String[] args) {
        AbstractFactory factory1 = new ConcreteFactory1();
        AbstractFactory factory2 = new ConcreteFactory2();
        ProductA productA1 = factory1.createProductA();
        ProductA productA2 = factory2.createProductA();
        ProductB productB1 = factory1.createProductB();
        ProductB productB2 = factory2.createProductB();
        productA1.methodA();
        productA2.methodA();
        productB1.methodB();
        productB2.methodB();
    }
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Fabrique_abstraite](https://fr.wikibooks.org/wiki/Patrons_de_conception/Fabrique_abstraite)