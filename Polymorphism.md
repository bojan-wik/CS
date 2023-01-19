#programming #java 

**Polimorfizm** (wielopostaciowość) to zagadnienie ściśle powiązane z dziedziczeniem ([[Inheritance]]). Sub-klasy mogą dziedziczyć stany (states) i zachowania (behaviours) swoich super-klas, ale także mogą je zmieniać za pomocą [[Method overriding]].

Innym sposobem w jaki może objawiać się polimorfizm w Javie jest [[Method overloading]]

## Przykład I

```java
class Movie {
    private String name;

    public Movie(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public String plot() {
        return "No plot here";
    }
}

class Jaws extends Movie {
    public Jaws() {
        super("Jaws");
    }

    @Override
    public String plot() {
        return "Shark attack poor people";
    }
}

class IndependenceDay extends Movie {
    public IndependenceDay() {
        super("Independence Day");
    }

    @Override
    public String plot() {
        return "Will Smith kicks aliens asses!";
    }
}

class KillBill extends Movie {
    public KillBill() {
        super("Kill Bill");
    }

    @Override
    public String plot() {
        return "Uma Thurman fights kung-fu";
    }
}

class StarWars extends Movie {
    public StarWars() {
        super("Star Wars");
    }

    @Override
    public String plot() {
        return "Jedi versus Sith";
    }
}

class Forgettable extends Movie {
    public Forgettable() {
        super("Forgettable");
    }

    // no plot() method
}

public class Main {

    public static Movie randomMovie() {
        int randomNumber = (int)(Math.random() * 5) + 1;
        System.out.printf("\nGenerated number: %d", randomNumber).println();
        switch (randomNumber) {
            case 1:
                return new Jaws();
            case 2:
                return new IndependenceDay();
            case 3:
                return new KillBill();
            case 4:
                return new StarWars();
            case 5:
                return new Forgettable();
        }
        return null;
    }

    public static void main(String[] args) {
        for (int i = 1; i <= 5; i ++) {
            Movie movie = randomMovie();
            System.out.printf("Movie #%d: '%s'", i, movie.getName()).println();
            System.out.printf("Plot: %s", movie.plot()).println();
        }
    }
}
```

## Przykład II

```java
class Animal {  
  
    public void makeSound() {  
        System.out.println("Unknown animal sound");  
    }  
}

class Dog extends Animal {  
  
    @Override  
    public void makeSound() {  
        System.out.println("woof woof");  
    }  
  
    public void fetch() {  
        System.out.println("fetch is fun!");  
    }  
}

class Cat extends Animal {  
  
    @Override  
    public void makeSound() {  
        System.out.println("meoooow");  
    }  
  
    public void scratch() {  
        System.out.println("I an a cat and I can scratch things.");  
    }  
}

class Main {  
  
    public static void main(String[] args) {  
        Dog luna = new Dog();  
        luna.makeSound();       // woof woof 
        luna.fetch();           // fetch is fun!
        feed(luna);             // Here's your dog food
  
        Animal gacek = new Dog();  
        gacek.makeSound();      // woof woof
        feed(gacek);            // Here's your dog food
  
        gacek = new Cat();  
        gacek.makeSound();      // meoooow
        ((Cat)gacek).scratch(); // I an a cat and I can scratch things.
        feed(gacek);            // Here's your cat food
    }  
  
    public static void feed(Animal animal) {  
        if (animal instanceof Dog) {  
            System.out.println("Here's your dog food");  
        }  
        else if (animal instanceof Cat) {  
            System.out.println("Here's your cat food");  
        }  
    }  
}
```

## Polymorphism Key Points

1. **Type vs Instance** - obiekt może jednocześnie posiadać typ superklasy i być instancją subklasy, np.:
```java
Animal gacek = new Dog();
```

2. **Access** - obiekty polimorficzne mają dostęp jedynie do memberów swojego typu (nie swojej instancji). Aby obiekt miał dostęp od memberów swojej instancji trzeba zastosować Castowanie ([[Casting]]), np.:
```java
gacek = new Cat();
((Cat)gacek).scratch();   // I an a cat and I can scratch things.
```

3. **Overridden methods**- jeśli metoda jest nadpisana przez subklasę to obiekt polimorficzny będzie wywoływał tą nadpisaną metodę, np.:
```java
gacek.makeSound();      // meoooow
```

4. **operator *instanceOf*** - odpowiada na pytanie: obiekt polimorficzny jest instancją jakiej klasy? np.:
```java
public static void feed(Animal animal) {  
    if (animal instanceof Dog) {  
        System.out.println("Here's your dog food");  
    }  
    else if (animal instanceof Cat) {  
        System.out.println("Here's your cat food");  
    }  
}
```

## Źródła:
- https://testautomationu.applitools.com/java-programming-course/chapter10.html