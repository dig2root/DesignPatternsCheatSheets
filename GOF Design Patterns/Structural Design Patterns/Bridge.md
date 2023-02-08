# Bridge

Bridge design pattern allows to separate an interface and its implementation.
It allows you to modify or change the implementation without modifying the client code.

## UML Class Diagram

![Bridge](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/dig2root/DesignPatternsCheatSheets/main/PlantUML/Bridge.puml? "The Bridge")

## Code Samples

### Java

```Java
package gof.structural.bridge;

public abstract class Abstraction {
    protected Implementor implementor;
    public void setImplementor(Implementor implementor) {
        this.implementor = implementor;
    }
    public abstract void operation();
}

public abstract class Implementor {
    public abstract void operation();
}

public class RefinedAbstraction extends Abstraction {
    @Override
    public void operation() {
        implementor.operation();
    }
}

public class ConcreteImplementorA extends Implementor {
    @Override
    public void operation() {
        // TODO Auto-generated method stub
    }
}

public class ConcreteImplementorB extends Implementor {
    @Override
    public void operation() {
        // TODO Auto-generated method stub
    }
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Pont](https://fr.wikibooks.org/wiki/Patrons_de_conception/Pont)