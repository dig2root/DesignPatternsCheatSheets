# Builder

_To do ..._

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

        @Override
        public Product getResult() {
            return product;
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

        @Override
        public Product getResult() {
            return product;
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