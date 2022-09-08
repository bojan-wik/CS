# Loops
#java 

## for & for-each loops
1. Pętli for i for-each używamy w przypadku kiedy wiemy ile razy mamy przeiterować. Przykład for-each loop:
```java
public static int countTrue(boolean[] array) {
        int trueValueCounter = 0;
        for (boolean element : array) {
            if (element == true) {
                trueValueCounter += 1;
            }
        }
        return trueValueCounter;
    }
```

2. To samo osiągnięte za pomocą zwykłej for loop:
```java
public static int countTrue(boolean[] array) {
        int trueValueCounter = 0;
        for (int i = 0; i < array.length; i += 1) {
            if (array[i] == true) {
                trueValueCounter += 1;
            }
        }
        return trueValueCounter;
    }
```

## while and do-while loops
1. Pętli while używamy, kiedy nie wiemy dokładnie ile ma być iteracji, tylko że pętla ma działać dopóki jakiś warunek jest spełniony (true).
```java
int count = 1;
while(count != 6) {
	System.out.println("Count value is " + count);
	count ++;
}
```
2. Pętli do-while użyjemy kiedy chcemy żeby zdefiniowany kod uruchomił się przynajmniej 1 raz
```java
int count = 1;
do {
    System.out.println("Count value was " + count);
    count ++;
} while(count != 6);
```
