# Builder

## UML Class Diagram

![Builder](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/dig2root/DesignPatternsCheatSheets/main/PlantUML/Builder.plantuml "The Builder")

## Code Samples

### Java

```Java
/* Produit */
class Pizza
{
    private String pate = "";
    private String sauce = "";
    private String garniture = "";

    public void setPate(String pate)          { this.pate = pate; }
    public void setSauce(String sauce)         { this.sauce = sauce; }
    public void setGarniture(String garniture) { this.garniture = garniture; }
}

/* Monteur */
abstract class MonteurPizza
{
    protected Pizza pizza;

    public Pizza getPizza() { return pizza; }
    public void creerNouvellePizza() { pizza = new Pizza(); }

    public abstract void monterPate();
    public abstract void monterSauce();
    public abstract void monterGarniture();
}

/* MonteurConcret */
class MonteurPizzaHawaii extends MonteurPizza
{
    public void monterPate()      { pizza.setPate("croisée"); }
    public void monterSauce()     { pizza.setSauce("douce"); }
    public void monterGarniture() { pizza.setGarniture("jambon+ananas"); }
}

/* MonteurConcret */
class MonteurPizzaPiquante extends MonteurPizza
{
    public void monterPate()      { pizza.setPate("feuilletée"); }
    public void monterSauce()     { pizza.setSauce("piquante"); }
    public void monterGarniture() { pizza.setGarniture("pepperoni+salami"); }
}

/* Directeur */
class Serveur
{
    private MonteurPizza monteurPizza;

    public void setMonteurPizza(MonteurPizza mp) { monteurPizza = mp; }
    public Pizza getPizza() { return monteurPizza.getPizza(); }

    public void construirePizza()
    {
        monteurPizza.creerNouvellePizza();
        monteurPizza.monterPate();
        monteurPizza.monterSauce();
        monteurPizza.monterGarniture();
    }
}

/* Un client commandant une pizza. */
class ExempleMonteur
{
    public static void main(String[] args)
    {
        Serveur serveur = new Serveur();
        MonteurPizza monteurPizzaHawaii  = new MonteurPizzaHawaii();
        MonteurPizza monteurPizzaPiquante = new MonteurPizzaPiquante();

        serveur.setMonteurPizza(monteurPizzaHawaii);
        serveur.construirePizza();

        Pizza pizza = serveur.getPizza();
    }
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Monteur](https://fr.wikibooks.org/wiki/Patrons_de_conception/Monteur)