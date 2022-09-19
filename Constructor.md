# Constructor
#programming #java 

## Co to jest?
[code](https://github.com/bojan-wik/SeleniumWithJavaCourse/blob/master/src/Chapter31_CoreJava2/c_Constructors1.java)

## Typy konstruktorów
[code](https://github.com/bojan-wik/SeleniumWithJavaCourse/blob/master/src/Chapter31_CoreJava2/c_Constructors2.java)

## this()
- Istnieje możliwość wywołania konstruktora wewn. innego konstruktora - za pomocą metody `this()`
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