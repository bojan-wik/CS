# Java Generics
#java 

#### Co to jest?
**Java Generics** (typy generyczne) - elementy pozwalające pisać kod w Javie bez wskazywania konkretnych typów danych, na których ten kod będzie operował.

W zależności od przekazywanego parametru możemy zmieniać zachowanie obiektu np. w listach, które w zależności od przyjmowanego parametru agregują konkretny typ danych, tzw. *parametrized types*.
```java
ArrayList<Integer> itemsOfParametrizedType = new ArrayList<>();
```
Listy bez sprecyzowanego w parametrze typu danych to tzw. *raw types* - cały czas można je pisać, ale nie jest to zalecane.
```java
ArrayList itemsOfRawType = new ArrayList();
```

#### Korzyści
- możliwość tworzenia bardziej elastycznego i zwięzłego kodu
- kontrola typów już na etapie pisania kodu (kompilacji/budowania), a nie dopiero w trakcie uruchomienia programu (runtime) - pozwala to znaleźć potencjalne bugi na wczesnym etapie
- przydatne w implementacji list, wielu algorytmów

