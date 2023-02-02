# Prototype

Prototype design pattern is used when creating an instance is complexe or takes time. Instead of creating several instances, the first one is cloned and the clone is modified as desired.

## UML Class Diagram

![Prototype](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/dig2root/DesignPatternsCheatSheets/main/PlantUML/Prototype.txt? "The Prototype")

## Code Samples

### Java

```Java
package gof.creational.prototype;

public class Prototype {

    public Prototype clone() {
        Prototype prototype = null;
        try {
            prototype = (Prototype) super.clone();
        } catch (CloneNotSupportedException e) {
            e.printStackTrace();
        }
        return prototype;
    }
}

public class ConcretePrototypeA extends Prototype {}

public class ConcretePrototypeB extends Prototype {}

public class Client {

    public static void main(String[] args) {
        Prototype prototypeA = new ConcretePrototypeA();
        Prototype prototypeB = new ConcretePrototypeB();
        Prototype clonePrototypeA = prototypeA.clone();
        Prototype clonePrototypeB = prototypeB.clone();
    }
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Prototype](https://fr.wikibooks.org/wiki/Patrons_de_conception/Prototype)
