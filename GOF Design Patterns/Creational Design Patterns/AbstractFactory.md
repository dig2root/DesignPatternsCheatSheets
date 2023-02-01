# Abstract factory

## UML Class Diagram

![Abstract factory](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/dig2root/DesignPatternsCheatSheets/main/PlantUML/AbstractFactory.plantuml "The Abstract Factory")

## Code Samples

### Java

```Java
/*
 * GUIFactory example
 */
public abstract class GUIFactory
{
    public static GUIFactory getFactory()
    {
        int sys = readFromConfigFile("OS_TYPE");
        if (sys == 0)
            return(new WinFactory());
        else
            return(new OSXFactory());
    }
    public abstract Button createButton();
}

class WinFactory extends GUIFactory
{
    public Button createButton()
    {
        return(new WinButton());
    }
}

class OSXFactory extends GUIFactory
{
    public Button createButton()
    {
        return(new OSXButton());
    }
}

public abstract class Button
{
    private String caption;
    public abstract void paint();
     
    public String getCaption()
    {
        return caption;
    }

    public void setCaption(String caption)
    {
        this.caption = caption;
    }
}
 
class WinButton extends Button
{
    public void paint()
    {
        System.out.println("I'm a WinButton: "+ getCaption());
    }
}

class OSXButton extends Button
{
    public void paint()
    {
        System.out.println("I'm a OSXButton: "+ getCaption());
    }
}

public class Application
{
    public static void main(String[] args)
    {
        GUIFactory aFactory = GUIFactory.getFactory();
        Button aButton = aFactory.createButton();
        aButton.setCaption("Play");
        aButton.paint();
    }
    // affiche :
    //   I'm a WinButton: Play
    // ou :
    //   I'm a OSXButton: Play
}
```

## Reference(s)

- [https://fr.wikibooks.org/wiki/Patrons_de_conception/Fabrique_abstraite](https://fr.wikibooks.org/wiki/Patrons_de_conception/Fabrique_abstraite)