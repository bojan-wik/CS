# for-each loop
#java 

Przykład for-each loop:
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

To samo osiągnięte za pomocą zwykłej for loop:
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