# Facade

The goal of Facade design pattern is to hide conception and/or an interface hard tu understance for a client.

## UML Class Diagram

![Facade](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/dig2root/DesignPatternsCheatSheets/main/PlantUML/Facade.puml? "The Facade")

## Code Samples

### Java

```Java
package gof.structural.facade;

public class Facade {
    private SubSystemA subSystemA;
    private SubSystemB subSystemB;
    private SubSystemC subSystemC;

    public Facade() {
        subSystemA = new SubSystemA();
        subSystemB = new SubSystemB();
        subSystemC = new SubSystemC();
    }

    public void methodA() {
        subSystemA.methodA();
        subSystemB.methodB();
    }

    public void methodB() {
        subSystemB.methodB();
        subSystemC.methodC();
    }
}

public class SubSystemA {
    public void methodA() {
        System.out.println("SubSystemA.methodA()");
    }
}

public class SubSystemB {
    public void methodB() {
        System.out.println("SubSystemB.methodB()");
    }
}

public class SubSystemC {
    public void methodC() {
        System.out.println("SubSystemC.methodC()");
    }
}

public class Client {
    public static void main(String[] args) {
        Facade facade = new Facade();
        facade.methodA();
        facade.methodB();
    }
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Façade](https://fr.wikibooks.org/wiki/Patrons_de_conception/Façade)