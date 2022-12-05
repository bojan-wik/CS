#programming #java 

## I. Co to jest?
[code](https://github.com/bojan-wik/SeleniumWithJavaCourse/blob/master/src/Chapter31_CoreJava2/c_Constructors1.java)

- w przypadku relacji superklasa-subklasa, gdy mamy tylko default konstruktory, w momencie utworzenia obiektu subklasy najpierw wywoływany jest konstruktor superklasy

## II. Typy konstruktorów
[code](https://github.com/bojan-wik/SeleniumWithJavaCourse/blob/master/src/Chapter31_CoreJava2/c_Constructors2.java)

## III. this() keyword
- Istnieje możliwość wywołania konstruktora wewn. innego konstruktora - za pomocą keyworda `this()`
- **Przykład użycia**: jeżeli user nie poda żadnych wartości i chcemy wywołać konstruktor z pre-definiowanymi wartościami. Wtedy z poziomu *pustego konstruktora* wywołujemy *sparametryzowany konstruktor* z pre-definiowanymi wartościami.
- `this()` musi być zawsze na samym początku, inaczej nie zadziała

```java
public BankAccount() {  
    this(123456789, 0.0, "Default name", "default@email.com", 123456789);  
    System.out.println("Empty constructor called");  
}  
  
public BankAccount(int number, double balance, String customerName, String customerEmail, int customerPhoneNumber) {    
    this.number = number;  
    this.balance = balance;  
    this.customerName = customerName;  
    this.customerEmail = customerEmail;  
    this.customerPhoneNumber = customerPhoneNumber;  
    System.out.println("Parametrized constructor called");
}
```

## IV. Dobre praktyki

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

### 2. W przypadku większej ilości konstruktorów używać keyworda this()
Czyli zdefiniować sobie najpierw bazowy, defaultowy konstruktor np:
```java
public Customer(String name, String email, int age) {
	this.name = name;
	this.email = email;
	this.age = age;
}
```
i potem kolejne konstruktory definiować w ten sposób:
```java
public Customer() {
	this("Default name", "default@email.com", 18)
}
```
a nie w ten sposób:
```java
public Customer(String name, String email, int age) {
	this.name = "Default name";
	this.email = "default@email.com";
	this.age = 18;
}
```

## Źródła:
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/3133106#overview