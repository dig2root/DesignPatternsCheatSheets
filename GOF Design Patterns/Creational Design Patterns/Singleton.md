# Singleton

The singleton is a design pattern where the goal is to **constraint** instanciation of a class to a unique object.

It is used when exactly one object is needed to perform operation in a system.
Generally the class constructor is _private_ or _protected_ to ensure instantiation only by the controlled method.

Be warned in multi-thread application where two or more threads execute the creation method at the same time.

## UML Class Diagram

![Singleton](https://upload.wikimedia.org/wikipedia/commons/f/f1/UML_DP_Singleton.png "The Singleton")

## Code Samples

### Java

```Java
public class Singleton
{
    /*
     * Création de l'instance au niveau de la variable.
     */
    private static final Singleton INSTANCE = new Singleton();

    /*
     * La présence d'un constructeur privé supprime
     * le constructeur public par défaut.
     */
    private Singleton() {}

    /*
     * Dans ce cas présent, le mot-clé synchronized n'est pas utile.
     * L'unique instanciation du singleton se fait avant
     * l'appel de la méthode getInstance(). Donc aucun risque d'accès concurrents.
     * Retourne l'instance du singleton.
     */
    public static Singleton getInstance()
    {
        return INSTANCE;
    }
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Singleton](https://fr.wikibooks.org/wiki/Patrons_de_conception/Singleton)