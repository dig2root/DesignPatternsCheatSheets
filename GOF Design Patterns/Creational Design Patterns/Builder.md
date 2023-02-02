# Builder

The Builder design pattern is a creational pattern that allows for the construction of complex objects step by step. 

The pattern consists of a **Builder** abstract class that defines the steps to be taken in the construction process, a **ConcreteBuilder** that implements these steps, a **Director** class that oversees the construction process and a **Product** that represents the final object being constructed.

This pattern is useful when the process of constructing an object is complicated and requires multiple steps, or when the final representation of the object can vary depending on the construction process.

## UML Class Diagram

![Builder](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/dig2root/DesignPatternsCheatSheets/main/PlantUML/Builder.puml? "The Builder")

## Code Samples

### Java

```Java
package gof.creational.builder;

public abstract class Builder {

        protected Product product;

        public abstract void buildPartA();
        public abstract void buildPartB();
        public abstract void buildPartC();

        public void create() {
            product = new Product();
        }

        public Product getResult() {
            return product;
        }
}

public class Product {

            private String partA;
            private String partB;
            private String partC;

            public void setPartA(String partA) {
                this.partA = partA;
            }
            public void setPartB(String partB) {
                this.partB = partB;
            }
            public void setPartC(String partC) {
                this.partC = partC;
            }
}

public class ConcreteBuilderA extends Builder {

        @Override
        public void buildPartA() {
            product.setPartA("part A.A");
        }

        @Override
        public void buildPartB() {
            product.setPartB("part A.B");
        }

        @Override
        public void buildPartC() {
            product.setPartC("part A.C");
        }
}

public class ConcreteBuilderB extends Builder {

        @Override
        public void buildPartA() {
            product.setPartA("part B.A");
        }

        @Override
        public void buildPartB() {
            product.setPartB("part B.B");
        }

        @Override
        public void buildPartC() {
            product.setPartC("part B.C");
        }
}

public class Director {

        public void buildProduct(Builder builder) {
            builder.create();
            builder.buildPartA();
            builder.buildPartB();
            builder.buildPartC();
        }
}

public class Client {

        public static void main(String[] args) {
            Director director = new Director();
            Builder builderA = new ConcreteBuilderA();
            Builder builderB = new ConcreteBuilderB();
            director.buildProduct(builderA);
            Product productA = builderA.getResult();
            director.buildProduct(builderB);
            Product productB = builderB.getResult();
        }
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Monteur](https://fr.wikibooks.org/wiki/Patrons_de_conception/Monteur)