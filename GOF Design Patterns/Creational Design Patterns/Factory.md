# Factory

## UML Class Diagram

![Factory](https://upload.wikimedia.org/wikipedia/commons/0/0c/UML_DP_Fabrique.png "The Factory")

## Code Samples

### Java

```Java
public class FabriqueAnimal
{
    private static FabriqueAnimal instance = new FabriqueAnimal();
    
    private FabriqueAnimal() {}

    public static FabriqueAnimal getFabriqueAnimalInstance() {
        return instance;
    }

    public Animal getAnimal(String typeAnimal) throws ExceptionCreation
    {
        if (typeAnimal.equals("chat"))
            return new Chat();
        else if (typeAnimal.equals("chien"))
            return new Chien();
        else
            throw new ExceptionCreation("Impossible de créer un " + typeAnimal);
    }
}

public abstract class Animal {
   public abstract void myName();
}

public class Chat extends Animal {
   @Override
   public void myName() {
     System.out.println("Je suis un Chat");
   }
}

public class Chien extends Animal {
   @Override
   public void myName() {
     System.out.println("Je suis un Chien");
   }
}

public class FabriqueExemple{
   public static void main(String [] args){
     FabriqueAnimal fabrique =  FabriqueAnimal.getFabriqueAnimalInstance();
     try {
       Animal animal = fabrique.getAnimal("chien");
       animal.myName();
     } catch(ExceptionCreation e) {
       e.printStackTrace();
     }
   }
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Fabrique](https://fr.wikibooks.org/wiki/Patrons_de_conception/Fabrique)