#programming #java 

**Exception** (wyjątek) - mechanizm wyjątków służy do obsługi błędów, które mogą wystąpić w czasie przebiegu programu. Wyjątek to odbiegnięcie od standardowego, zaplanowanego przebiegu programu powodując jego 'wywalenie'.

## Sposoby obsługi wyjątków

W programowaniu istnieją dwa główne podejścia do radzenia sobie z wyjątkami:
- **LBYL** (Look Before You Leap - rozejrzyj się zanim skoczysz) - częściej używany w Javie
- **EAFP** (it's Easier to Ask Forgiveness than Permission) - tzw. try-catch-finally block

### Przykład: 
Dzielenie przez zero jest niedozwolone.

Przy próbie dzielenia przez zero taka metoda:
```java
private static int divide(int x, int y) {
        return x / y;
    }
```
wywali mi ``ArithmeticException``

#### Podejście LBYL
```java
private static int divideLBYL(int x, int y) {
        if (y != 0) {
            return x / y;
        } else {
            return 0;
        }
    }
```

#### Podejście EAFP
```java
private static int divideEAFP(int x, int y) {
        try {
            return x / y;
        } catch (ArithmeticException arithmeticException) {
            return 0;
        }
    }
```

Try-catch-finally block:
- **try** - tu ląduje kod, który może powodowować problemy (wywoływać exceptiony) 
- **catch** - tu definuję exception jaki ma być wyłapywany i sposób w jaki ma być obsłużony
	- wyłapywany jest exception danej klasy i wszystkie jej sub-klasy
- **finally** - jeżeli jakiś exception zostanie wyłapany w sekcji *try* to kod z tej sekcji nie jest wykonywany dalej tylko program od razu przeskakuje do sekcji *catch* - w sekcji *finally* ląduje kod, który ma być wykonany po wyłapaniu exceptiona

Sekcje *try* i *finally* są opcjonalne, tzn. musi występować przynajmniej jedna z nich.

### Inne przykłady: 
- [UdemyJavaMasterclass/src/section14/exceptions at master · bojan-wik/UdemyJavaMasterclass · GitHub](https://github.com/bojan-wik/UdemyJavaMasterclass/tree/master/src/section14/exceptions)

## Źródła:
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/4859500#overview