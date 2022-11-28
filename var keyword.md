#programming #java 

## var

**Java** jest językiem **typowanym statycznie** tzn. musimy określić typ zmiennej, którą definiujemy, np.:
```java
String name = "Wiktor";
int iq = 200;
```

Wiele języków, takich jak np. Python, JavaScript jest językami **typowanymi dynamicznie**, czyli nie musimy określać typu zmiennej. Ponadto nie jest problemem to, że do zmiennej, do której najpierw przypisaliśmy np. liczbę po chwili przypiszemy String, np.:
```javascript
var name = "Wiktor";
name = 150;
```

Java 10 wprowadziła możliwość używania keyworda **var**, który umożliwia skrócenie deklaracji zmiennych, np.:
```java
var name = "Wiktor";
```
Typ zmiennej zostanie wywnioskowany na podstawie tego co do niej przypisaliśmy, w tym przypadku String. Mechanizm ten nazywa się **type inference**.

## Type inference
- to nie to samo co typowanie dynamiczne, bo nie możemy do zmiennej, która najpierw jest np. Stringiem potem przypisać np. inta
- działa tylko dla zmiennych lokalnych ([[variable]])
- zmienne muszą być zadeklarowane i od razu zainicjalizowane ([[Declaration vs. Initialization]])
- nie może być użyte jako parametry metody albo return type

## Źródła
- https://testautomationu.applitools.com/java-programming-course/chapter8a.html
- https://javastart.pl/baza-wiedzy/slownik/slowo-kluczowe-var