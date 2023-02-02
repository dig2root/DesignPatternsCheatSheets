# Singleton

The singleton is a design pattern where the goal is to **constraint** instanciation of a class to a unique object.

It is used when exactly one object is needed to perform operation in a system.
Generally the class constructor is _private_ or _protected_ to ensure instantiation only by the controlled method.

Be warned in multi-thread application where two or more threads execute the creation method at the same time.

## UML Class Diagram

![Singleton](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/dig2root/DesignPatternsCheatSheets/main/PlantUML/Singleton.txt? "The Singleton")

## Code Samples

### Java

```Java
package gof.creational.singleton;

public class Singleton {

    // The instance is created when the class is loaded
    private static final Singleton INSTANCE = new Singleton();

    // The constructor is private to prevent instantiation
    private Singleton() {}

    // The instance is returned by this method
    public static Singleton getInstance() {
        return INSTANCE;
    }
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Singleton](https://fr.wikibooks.org/wiki/Patrons_de_conception/Singleton)