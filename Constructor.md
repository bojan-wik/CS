#programming #java 

## I. Co to jest?
[code](https://github.com/bojan-wik/SeleniumWithJavaCourse/blob/master/src/Chapter31_CoreJava2/c_Constructors1.java)

## II. Typy konstruktorów
[code](https://github.com/bojan-wik/SeleniumWithJavaCourse/blob/master/src/Chapter31_CoreJava2/c_Constructors2.java)

## III. this() vs super() method calls
- zarówno `this()` jak i `super()` muszą być na samym początku, inaczej nie zadziałają
- nie można jednocześnie wykorzystywać obu
- to nie to samo co [[this vs super keywords]]

### 1. this() method call
- `this()` wykorzystuje się w obrębie bieżącej klasy
- służy do wywołania konstruktora z poziomu innego konstruktora

**Przykład użycia**: jeżeli user nie poda żadnych wartości i chcemy wywołać konstruktor z pre-definiowanymi wartościami. Wtedy z poziomu *pustego konstruktora* wywołujemy *sparametryzowany bazowy konstruktor* z pre-definiowanymi wartościami.

```java
public Customer() {
	this("Default name", "default@email.com", 0)
}

public Customer(String name, String email, int age) {
	this.name = name;
	this.email = email;
	this.age = age;
}
```

### 2. super() method call
- `super()` wykorzystuje się w relacji superklasa - subklasa
- służy do wywołania konstruktora super-klasy z poziomu konstruktora sub-klasy

```java
class Person {  
  
    public Person() {  
        System.out.println("Person default-constructor called");  
    }  
  
    public Person(String name) {  
        System.out.println("Person constructor(String name) called");  
    }  
}  
  
class Employee extends Person {  
  
    public Employee() {  
        System.out.println("Employee default-constructor called");  
    }  
  
    public Employee(String name) {  
        super(name);  
        System.out.println("Employee constructor(String name) called");  
    }  
}  
  
class Main {  
  
    public static void main(String[] args) {  
        Employee employee1 = new Employee();  
        /* OUTPUT:  
        Person default-constructor called        
        Employee default-constructor called 
        */  
        Employee employee2 = new Employee("Wiktor");  
        /* OUTPUT:  
        Person constructor(String name) called        
        Employee constructor(String name) called 
        */    
    }  
}
```

- gdy mamy tylko defaultowe konstruktory, w momencie utworzenia obiektu sub-klasy najpierw wywoływany jest konstruktor super-klasy, a `super()` jest dodany automatycznie 
- jeżeli super-klasa nie ma defaultowego konstruktora, sub-klasa musi za pomocą `super()` wywołać  jeden z jej sparametryzowanych konstruktorów

## IV. private conctructor

Jeżeli chcę zablokować możliwość tworzenia instancji danej klasy to konstruktor tej klasy oznaczam jako `private`, np. jest to tak zrobione we wbudowanej klasie `Math`:

```java
public final class Math {  
  
    // Don't let anyone instantiate this class.    
     private Math() {}  
  
     public static final double E = 2.7182818284590452354;
}
```

## V. Dobre praktyki

### 1. Inicjalizować fieldy bezpośrednio w konstruktorze a nie za pomocą setterów 
Czyli robić tak:
```java
public Customer(String name, String email) {
	this.name = name;
	this.email = email;
}
```
a nie tak:
```java
public Customer(String name, String email) {
	setName(name);
	setEmail(email);
}
```
bo może to rodzić problemy, gdy mamy dziedziczenie pomiędzy klasami i settery mogą nie wywoływać się poprawnie.

### 2. Constructor chaining
czyli w przypadku większej ilości konstruktorów używać metod this(), super()

#### this() example
```java
public class Rectangle {  
  
    private int x;  
    private int y;  
    private int width;  
    private int height;  
  
    // 1szy konstruktor  
    public Rectangle() {  
        this(0, 0); // wywołuje 2gi konstruktor  
    }  
  
    // 2gi konstruktor  
    public Rectangle(int width, int height) {  
        this(0, 0, width, height); // wywoułuje 3ci konstruktor  
    }  
  
    // 3ci - bazowy konstruktor  
    public Rectangle(int x, int y, int width, int height) {  
        // inicjalizuje fieldy  
        this.x = x;  
        this.y = y;  
        this.width = width;  
        this.height = height;  
    }  
}
```

#### this() + super() example
```java
class Shape {  
  
    private int x;  
    private int y;  
  
    public Shape(int x, int y) {  
        this.x = x;  
        this.y = y;  
    }  
}  
  
class Square extends Shape {  
  
    private int width;  
    private int height;  
  
    public Square(int x, int y) {  
        this(x, y, 0, 0);  
    }  
  
    public Square(int x, int y, int width, int height) {  
        super(x, y);  
        this.width = width;  
        this.height = height;  
    }  
}
```

Constructor chaining pozwala uniknąć duplikowania kodu.

### 3. Unikać Constructor Telescoping Pattern, preferować zamiast tego Building Pattern
>https://app.pluralsight.com/course-player?clipId=e885817c-b774-4782-8ebb-115957e01229

## Źródła:
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/3133106#overview
- https://testautomationu.applitools.com/java-programming-course/chapter9b.html