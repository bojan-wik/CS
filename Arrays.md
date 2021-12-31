# Arrays
#java 

## Concatenating two int arrays
Nie jest to możliwe za pomocą żadnej wbudowanej metody, ale mogę to zrobić np. w taki sposób:
```java
public static int[] concat(int[] array1, int[] array2) {
        int[] arrayConcatenated = new int[array1.length + array2.length];
        int count = 0;
        for (int i = 0; i < array1.length; i += 1) {
            arrayConcatenated[count] = array1[i];
            count += 1;
        }
        for (int j = 0; j < array2.length; j += 1) {
            arrayConcatenated[count] = array2[j];
            count += 1;
        }
        return arrayConcatenated;
    }
```
Dla Stringów rozwiązanie może wyglądać trochę inaczej:
https://www.tutorialspoint.com/javaexamples/arrays_merge.htm

---
https://edabit.com/challenge/E2WdAPmgNJnbL5RvF