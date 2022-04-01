# Relationships between classes
#java 

## Inheritance, composition, aggregation
Na przykładzie parent-klasy 'Car'

```java
public class Car {

    // common car fields (states)
    private String model;
    private int maxSpeed;
    private int yearOfManufacture;

    // constructor
    public Car(String model, int maxSpeed, int yearOfManufacture) {
        this.model = model;
        this.maxSpeed = maxSpeed;
        this.yearOfManufacture = yearOfManufacture;
    }

    // common car methods (behaviours)
    public void gas() {
        System.out.printf("%s: gas\n", this.model);
    }
    public void brake() {
        System.out.printf("%s: brake\n", this.model);
    }

    // getters
    public String getModel(){
        return this.model;
    }
    public int getMaxSpeed() {
        return this.maxSpeed;
    }
    public int getYearOfManufacture() {
        return this.yearOfManufacture;
    }
}
```

i jej child-klas, które reprezentują konkretne pojazdy
```java
public class Sedan extends Car {

    public Sedan(String model, int maxSpeed, int yearOfManufacture) {
        super(model, maxSpeed, yearOfManufacture);
    }
```

```java
public class F1Car extends Car {

    public F1Car(String model, int maxSpeed, int yearOfManufacture) {
        super(model, maxSpeed, yearOfManufacture);
    }

    // method/behaviour unique for F1Car
    public void pitStop() {
        System.out.println("pit stop");
    }
}
```

Klasy i objekty mogą być ze sobą łączone tworząc relacje typu:
* is-a
* has-a

#### Inheritance
[[Inheritance]] opisuje relację typu "is-a" np. relacja car-sedan. Sedan is a car.
'Car' to parent-klasa, 'Sedan' to child-klasa.

#### Composition and aggregation
[[Composition]] and aggregation opisują relację typu "has-a" np.
1. Każdy samochód ma silnik - przykład composition.
Silnik jest częścią konkretnego samochodu i nie może być jednocześnie częścią innego samochodu, czyli obiekt jest częścią jakiegoś konkretnego obiektu i nie może być jednocześnie częścią innego obiektu tego samego typu.

2. Każdy samochód może mieć pasażerów - przykład aggregation.
Fakt, że pasażer A jest w samochodzie, nie znaczy, że nie ma tam też pasażera B i C.

W momencie kiedy zastanawiamy się, czy użyć Inheritance, czy Composition, generalna zasada mówi o tym, żeby w pierwszej kolejności rozpatrywać Composition, która daje więcej elastyczności.

---
https://codegym.cc/groups/posts/96-relationships-between-classes-inheritance-composition-and-aggregation



