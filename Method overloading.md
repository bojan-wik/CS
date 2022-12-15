#programming #java

Ficzer który pozwala na istnienie wielu metod o tej samej nazwie w obrębie:
- jednej klasy 
- w obrębie relacji superklasa <-> subklasa

Jest to możliwe gdy: 
-   data typy parametrów są inne,
-   liczba parametrów jest inna,
-   data typy i liczba parametrów jest inna.

```java
public class Main {

    public static int calculateScore(String playerName, int score) {
        System.out.printf("Player %s scored %d", playerName, score).println();
        return score * 1000;
    }

    public static int calculateScore(int score) {
        System.out.printf("Unnamed Player scored %d", score).println();
        return score * 1000;
    }

    public static int calculateScore() {
        System.out.printf("No player name, no player score").println();
        return 0;
    }

    public static void main(String[] args) {
        calculateScore("Wiktor", 500);
        calculateScore(100);
        calculateScore();
    }
}
```

```
Player Wiktor scored 500
Unnamed Player scored 100
No player name, no player score
```

Często korzystanie z mechanizmu overloadingu jest postrzegane jako **dobra praktyka** np. pisanie metody do sumowania liczb. Tworzę wiele metod o tej samej nazwie sum(), tylko z inną liczbą parametrów, w zależności ile liczb dana metoda będzie sumować.

##### Korzyści:
1. Poprawia czytelność i re-używalność kodu
2. Łatwiej jest zapamiętać jedną nazwę metody
3. Pozwala osiągnąć spójność w nazewnictwie
4. Daje więcej elastyczności w programowaniu