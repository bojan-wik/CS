# Exceptions
#programming #java 

W programowaniu istnieją dwa główne podejścia do radzenia sobie z errorami:
- **LBYL** (Look Before You Leap - rozejrzyj się zanim skoczysz) - częściej używany w Javie
- **EAFP** (it's Easier to Ask Forgiveness than Permission)

Try-catch block:
- **try** - tu ląduje kod, który może powodowować problemy (wywoływać exceptiony) 
- **catch** - tu definuję exception jaki ma być wyłapywany i sposób w jaki ma być obsłużony

##### Przykład: 
Dzielenie przez zero jest niedozwolone.

Przy próbie dzielenia przez zero taka metoda:
```java
private static int divide(int x, int y) {
        return x / y;
    }
```
wywali mi ``ArithmeticException``

##### Podejście LBYL
```java
private static int divideLBYL(int x, int y) {
        if (y != 0) {
            return x / y;
        } else {
            return 0;
        }
    }
```

##### Podejście EAFP
```java
private static int divideEAFP(int x, int y) {
        try {
            return x / y;
        } catch (ArithmeticException arithmeticException) {
            return 0;
        }
    }
```