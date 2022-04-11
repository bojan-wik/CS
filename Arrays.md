# Arrays
#java 

## Inicjalizowanie - 3 sposoby
```java
// 1  
int[] firstArr = new int[3];  
firstArr[0] = 5;  
firstArr[1] = 10;  
firstArr[2] = 15;  
  
// 2  
int[] secondArr = {100, 200, 300};  
  
// 3  
int[] thirdArr = new int[3];  
for (int i = 0; i < thirdArr.length; i ++) {  
 thirdArr[i] = i * 20;  
}
```

#### Sorting int array DESC
```java
public static int[] sortIntegers(int[] array) {
        int[] sortedArray = Arrays.copyOf(array, array.length);
        boolean flag = true;
        int temp;
        while (flag) {
            flag = false;
            for (int i = 0; i < sortedArray.length - 1; i ++) {
                if (sortedArray[i] < sortedArray[i+1]) {
                    temp = sortedArray[i];
                    sortedArray[i] = sortedArray[i+1];
                    sortedArray[i+1] = temp;
                    flag = true;
                }
            }
        }
        return sortedArray;
    }
```
>https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/3323782#content

#### Concatenating two int arrays
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
>https://edabit.com/challenge/E2WdAPmgNJnbL5RvF

Dla Stringów rozwiązanie może wyglądać trochę inaczej:
https://www.tutorialspoint.com/javaexamples/arrays_merge.htm

