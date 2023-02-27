#programming #java 

**Exception** (wyjątek) - mechanizm wyjątków służy do obsługi błędów, które mogą wystąpić w czasie przebiegu programu. Wyjątek to odbiegnięcie od standardowego, zaplanowanego przebiegu programu powodując jego 'wywalenie'.

## Sposoby obsługi wyjątków

W programowaniu istnieją dwa główne podejścia do radzenia sobie z wyjątkami:
- **LBYL** (Look Before You Leap - rozejrzyj się zanim skoczysz) - częściej używany w Javie
- **EAFP** (it's Easier to Ask Forgiveness than Permission) - catching the exception

### Przykład: 
Dzielenie przez zero jest niedozwolone.

Przy próbie dzielenia przez zero taka metoda:
```java
private static int divide(int x, int y) {
        return x / y;
    }
```
wywali mi ``ArithmeticException``

### I. Podejście LBYL
```java
private static int divideLBYL(int x, int y) {
        if (y != 0) {
            return x / y;
        } else {
            return 0;
        }
    }
```

### II. Podejście EAFP (catching the exception)
```java
private static int divideEAFP(int x, int y) {
        try {
            return x / y;
        } catch (ArithmeticException arithmeticException) {
            return 0;
        }
    }
```

#### Catching the exception - sposoby:

##### 1. try-catch-finally:
- **try** - tu ląduje kod, który może powodowować problemy (wywoływać exceptiony) 
- **catch** - tu definuję exception jaki ma być wyłapywany i sposób w jaki ma być obsłużony
	- wyłapywany jest exception danej klasy i wszystkie jej sub-klasy
	- w obrębie jednego bloku catch można zdefiniować >1 exceptionów, oddzielonych znakiem `|`, np. `catch (IOException | ParseException e) {e.printStackTrace();}`
	- może być >1 bloków catch
- **finally** - jeżeli jakiś exception zostanie wyłapany w sekcji *try* to kod z tej sekcji nie jest wykonywany dalej tylko program od razu przeskakuje do sekcji *catch* - w sekcji *finally* ląduje kod, który ma być wykonany po wyłapaniu exceptiona **ALE** ten kod będzie wykonany także, gdy żaden exception nie zostanie wyłapany

Sekcje *try* i *finally* są opcjonalne, tzn. musi występować przynajmniej jedna z nich.

##### 2. [[try-with-resources]]

### III. Rethrowing the exception
Poza wyłapywaniem i obsługiwaniem exceptionów możliwe jest też ich ponowne 'wyrzucenie'.

Dodajemy keyword `throws` do headera metody i określamy exception
```java
public static void createNewFileRethrow() throws IOException {  
    file = new File("resources/nonexistent.txt");  
    file.createNewFile();  
}
```

Exception sam w sobie nie jest obsługiwany, tylko jest 'przerzucany wyżej' w call stacku, czyli jak jakaś metoda np. main() wywołuje ww. metodę createNewFileRethrow() to teraz po stronie metody main() leży sposób na poradzenie sobie z przerzuconym na nią wyjątkiem. Może go wyłapać i obsłużyć (try-catch-finally) albo przerzucić go jeszcze wyżej.

```java
public static void main(String[] args) throws IOException {  
        createNewFileRethrow();  
    }
```

### Inne przykłady: 
- [UdemyJavaMasterclass/src/section14/exceptions at master · bojan-wik/UdemyJavaMasterclass · GitHub](https://github.com/bojan-wik/UdemyJavaMasterclass/tree/master/src/section14/exceptions)

## Źródła:
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/4859500#overview
- https://testautomationu.applitools.com/java-programming-course/chapter13a.html