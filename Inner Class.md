#java #programming

## I. Definicja i rodzaje

**Inner class** - klasa utworzona wewnątrz innej klasy/interfejsu.

**Rodzaje:**
- (standard) inner class
- local inner classes
- anonymous inner classes

## II. (standard) inner class

Generalnie *inner class* używa się, aby poprawić [[Encapsulation]] w kodzie. Jeżeli mamy jakąś klasę, która stanowi część innej klasy, wystarczy, że komunikuje się tylko z nią i nie musi być dostępna na zewnątrz, to wtedy warto zastosować *inner class*. Z tego też powodu *inner class* jest najczęściej deklarowana jako **private**.

Gdyby jednak była zadeklarowana jako **public** to wtedy dostęp do niej z poziomu innej klasy wyglądałby tak (na przykładzie kodu z poniżej):
```java
// outerClass.innerClass innerClass_instance = outerClass_instance.new innerClass();  
Gearbox.Gear gear1 = skodaGearbox.new Gear(1, 12.3);
```

Ważne jest także to, że klasa wewnętrzna ma dostęp do wszystkich atrybutów czy metod klasy zewnętrznej, w której została zdefiniowana.

### Przykłady użycia

#### Plain Java

Skrzynia biegów w samochodzie i poszczególne biegi tej skrzyni.
1. Skrzynia biegów - modelujemy jako standardową klasę (zewnętrzną)
2. Bieg - modelujemy jako klasę wewnętrzną. Generalnie biegi skrzyni rozpatrujemy tylko w kontekście całej skrzyni biegów. W oderwaniu od niej, jako pojedyńcze biegi nie stanowią dla nas żadnej wartości. Dlatego też w tym przypadku warto biegi zamodelować jako inner class.

```java
// OUTER CLASS
public class Gearbox {  
  
    private ArrayList<Gear> gears;  
    private int maxGears;  
    private int currentGear = 0; // skrzynia biegów ustawiona na luz  
    private boolean clutchIsIn = false;  
  
    public Gearbox(int maxGears) {  
        this.maxGears = maxGears;  
        gears = new ArrayList<>();  
  
        for (int i = 0; i < maxGears; i ++) {  
            addGear(i, i * 5.3);  
        }  
    }  
   
    private void addGear(int gearNumber, double ratio) {  
        if (gearNumber > 0 && gearNumber <= maxGears) {  
            gears.add(new Gear(gearNumber, ratio));  
        }  
    }  
  
   public void changeGear(int newGear) {  
        if (newGear >= 0 && newGear <= gears.size() && clutchIsIn) {  
            currentGear = newGear;  
            System.out.println("Gear " + newGear + " selected");  
        } else {  
            System.out.println("Grind!");  
            currentGear = 0;  
        }  
   }  
  
    public void operateClutch(boolean in) {  
        clutchIsIn = in;  
    }  
  
   public double getWheelSpeed(int revs) {  
        if (clutchIsIn) {  
            System.out.println("The clutch is in and the car is not moving.");  
            return 0.0;  
        }  
        return revs * gears.get(currentGear).getRatio();  
   }  
  
    // INNER CLASS  
    private class Gear {  
  
        private int gearNumber;  
        private double ratio;  
  
        public Gear(int gearNumber, double ratio) {  
            this.gearNumber = gearNumber;  
            this.ratio = ratio;  
        }  
  
        public double getRatio() {  
            return ratio;  
        }  
    }  
}
```

#### Testy automatyczne

W myśl [[Page Object Pattern]] strona https://the-internet.herokuapp.com/hovers została zamodelowana jako osobna klasa - standardowa klasa zewn.

Na stronie znajdują się 3 obrazki symbolizujące userów. Po najechaniu na każdy z obrazków pojawiają się dodatkowe informacje o userze: name i link view profile.

Te dodatkowe informacje - name i link view profile, zostały zamodelowane jako **inner class**.
W tym przypadku inner class zadeklarowana jest jako public, ponieważ jest bezpośrednio wykorzystywana testach (w odrębnej klasie testowej).

![[Pasted image 20221117105954.png]]

---
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/3751972#notes
- https://testautomationu.applitools.com/selenium-webdriver-tutorial-java/chapter5.html


## III. local inner class

- Inner class, które definiujemy wewnątrz bloku kodu (wewnątrz metody, bloku if itp.).
- Nie poprzedzają ich żadne [[Access modifiers]] (public, private, protected)
- Żadko używane

```java
public static void main(String[] args) {  
  
    // LOCAL INNER CLASS  
    class ClickListener implements Button.OnClickListener {  
  
        public ClickListener() {  
            System.out.println("Listener connected to the button");  
        }  
  
        @Override  
        public void onClick(String title) {  
            System.out.println(title + " button was clicked");  
        }  
    }  
  
    btnSave.setOnClickListener(new ClickListener());  
}
```

## IV. anonymous inner class

- to też local inner class
- nie mają nazwy
- deklarujemy klasę i tworzymy jej instancję w tym samym momencie - jest tylko jedna instancja klasy
- używane częściej niż zwykłe local inner class (np. dla event handlerów przy buttonach w UI), ale i tak pewnie w testach automatycznych praktycznie nie używane

```java
public static void main(String[] args) {  

    // ANONYMOUS INNER CLASS  
    btnSave.setOnClickListener(new Button.OnClickListener() {  
        @Override  
        public void onClick(String title) {  
            System.out.println(title + "button was clicked");  
        }  
    });
}
```
---
* https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/3751972#notes