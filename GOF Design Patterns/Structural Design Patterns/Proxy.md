# Proxy

## UML Class Diagram

![Proxy](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/dig2root/DesignPatternsCheatSheets/main/PlantUML/Proxy.puml? "The Proxy")

## Code Samples

### Java

```Java
package gof.structural.proxy;

public interface IObject {
    void methodA();
    void methodB();
}

public class Proxy implements IObject {
    private IObject object;

    public Proxy() {
        object = new Object();
    }

    public void methodA() {
        object.methodA();
    }

    public void methodB() {
        object.methodB();
    }
}

public class Object implements IObject {
    public void methodA() {
        System.out.println("Object.methodA()");
    }

    public void methodB() {
        System.out.println("Object.methodB()");
    }
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Proxy](https://fr.wikibooks.org/wiki/Patrons_de_conception/Proxy)