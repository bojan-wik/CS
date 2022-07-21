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

Dzięki typom sparametryzowanym możemy walidować rodzaj wprowadzanych danych. Tutaj klasa *Team* jako parametr przyjmuje tylko i wyłącznie klasy, które są sub-klasami dla klasy *Parent*.
```java
public class Team<T extends Player> {
	private ArrayList<T> members = new ArrayList<>();
}
```

```java
public static void main(String[] args) {
        FootballPlayer footballPlayer1 = new FootballPlayer("Vic");

        Team<FootballPlayer> footballTeam = new Team<>("Football Team");
        footballTeam.addPlayer(footballPlayer1);
        // to da errory, jako że ta instancja do klasy 'Team' przyjmuje parametr typu 'FootballPlayer'
//        footballTeam.addPlayer(baseballPlayer1);
//        footballTeam.addPlayer(soccerPlayer1);
}
```

Jako *type parameter* możemy przekazywać klasy albo interfejsy - zawsze w tej kolejności, najpierw klasa, potem interface.
```java
public class Team<T extends Player & Coach & Manager> {
	private ArrayList<T> members = new ArrayList<>();
}
```
*Coach* i *Manager* w tym przypadku to interfejsy.


#### Korzyści
- możliwość tworzenia bardziej elastycznego i zwięzłego kodu
- kontrola typów już na etapie pisania kodu (kompilacji/budowania), a nie dopiero w trakcie uruchomienia programu (runtime) - pozwala to znaleźć potencjalne bugi na wczesnym etapie
- przydatne w implementacji list, wielu algorytmów

---
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/3824746#overview
- https://github.com/bojan-wik/UdemyJavaMasterclass/tree/master/src/section10/javaGenerics