# Prototype



## UML Class Diagram

![Prototype](https://upload.wikimedia.org/wikipedia/commons/b/bd/UML_DP_Prototype.png "The Prototype")

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