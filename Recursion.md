# Recursion
#programming #java 

Rekursję/rekurencję można wyjaśnić na przykładzie zadania na znalezienie silni (factorial) jakiejś liczby.

Silnia liczby n, oznaczanej jako n!, to wartość iloczynu wszystkich liczb naturalnych od 1 do n.
np.
1! = 1
2! = 1 x2 = 2
3! = 1 x 2 x 3 = 6
itd.
wyjątek stanowi silnia liczby 0, która wynosi 1
0! = 1

#### Rozwiązanie na znalezienie silni bez użycia rekursji
```java
public static int getFactorial(int number) {
        int factorial = 1;
        for (int i = 1; i <= number; i++) {
            factorial = factorial * i;
        }
        return factorial;
    }
```

#### Rozwiązanie na znalezienie silni z użyciem rekursji
```java
public static int getFactorialRecursively(int number) {
        if (number <= 1) {
            return 1;
        } else {
            return number * getFactorialRecursively(number - 1);
        }
    }
```

**Rekursja** zachodzi w momencie, kiedy metoda wywołuje samą siebie. Wtedy jest to metoda rekursywna/rekurencyjna. Z reguły składa się z dwóch części:
1. Warunek kończący - gdy warunek kończący jest spełniony, metoda przestaje wywoływać samą siebie i zaczyna przekazywać wartości 'w górę'. Kiedy nie ma warunku kończącego zachodzi nieskończona pętla, w której metoda będzie wywoływała się do momentu otrzymania [[StackOverflowError]]
2. Logika, której wymaga sytuacja oraz wywołanie rekursji, ale z inną wartością wejściową

czyli
```java
public static int getFactorialRecursively(int number) {
		// warunek kończący - gdy osiągniemy liczbę 1
        if (number <= 1) {
            return 1;
		// jeżeli liczba nie jest równa 1, to mnożymy aktualną liczbę przez wynik kolejnego rekursywnego wywołania metody
        } else {
            return number * getFactorialRecursively(number - 1);
        }
    }
```