# Prototype



## UML Class Diagram

![Prototype](https://upload.wikimedia.org/wikipedia/commons/b/bd/UML_DP_Prototype.png "The Prototype")

## Code Samples

### Java

```Java
/* Classe Prototype */
public class Cookie implements Cloneable
{
    public Cookie clone()
    {
        try {
            Cookie copy = (Cookie)super.clone();
            // Dans une implémentation réelle de ce patron de conception, il faudrait
            // créer la copie en dupliquant les objets contenus et en attribuants des
            // valeurs valides (exemple : un nouvel identificateur unique pour la copie).
            return copy;
        } catch (CloneNotSupportedException e) {
            return null;
        }
    }
}

/* Prototype concrets à copier */
public class CoconutCookie extends Cookie { }

/* Classe utilisatrice */
public class CookieMachine
{
    private Cookie cookie; // peut aussi être déclaré comme : private Cloneable cookie;

    public CookieMachine(Cookie cookie)
    { 
        this.cookie = cookie; 
    }

    public Cookie makeCookie()
    {
        return cookie.clone(); 
    }

    public static void main(String args[])
    { 
        Cookie        tempCookie =  null; 
        Cookie        prot       = new CoconutCookie(); 
        CookieMachine cm         = new CookieMachine(prot); 

        for (int i=0; i<100; i++)
            tempCookie = cm.makeCookie(); 
    }
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Prototype](https://fr.wikibooks.org/wiki/Patrons_de_conception/Prototype)