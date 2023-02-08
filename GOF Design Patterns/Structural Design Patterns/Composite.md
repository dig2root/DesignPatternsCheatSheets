# Composite

## UML Class Diagram

![Composite](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/dig2root/DesignPatternsCheatSheets/main/PlantUML/Composite.puml? "The Composite")

## Code Samples

### Java

```Java
package gof.structural.composite;

import java.util.ArrayList;
import java.util.List;

public abstract class Object {
    public abstract void operation();
    public abstract void add(Object object);
    public abstract void remove(Object object);
    public abstract List<Object> getObjects();
}

public class ObjectComposite implements Object {
    private List<Object> objects = new ArrayList<Object>();

    public void operation() {
        for (Object object : objects) {
            object.operation();
        }
    }

    public void add(Object object) {
        objects.add(object);
    }

    public void remove(Object object) {
        objects.remove(object);
    }

    public List<Object> getObjects() {
        return objects;
    }
}

public class ObjectLeaf implements Object {
    private String name;

    public ObjectLeaf(String name) {
        this.name = name;
    }

    public void operation() {
        System.out.println(name);
    }
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Objet_composite](https://fr.wikibooks.org/wiki/Patrons_de_conception/Objet_composite)