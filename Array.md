#java 

## I. Inicjalizowanie - 3 sposoby
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

#### Multidimensional arrays
|       | column 0 | column 1 |
| ----- | -------- | -------- |
| row 0 | 2        | 4        |
| row 1 | 6        | 8         |

```java
// 1st argument stands for number of rows, 2nd for number of columns 
int[][] arr2D = new int[2][2] 

arr2D[0][0] = 2; 
arr2D[0][1] = 4; 
arr2D[1][0] = 6; 
arr2D[1][1] = 8;
```
## II. Printowanie arraya
1. Za pomocą [[toString() method]]
```java
System.out.println(Arrays.toString(firstArr));
```

2. Za pomocą for-loop
```java
//tbd
```

## III. Code snippets

### Join/concatenate a String array into single String
```java
String[] words = {"Hello", "my", "friend"}
String sentence = String.join(" ", words);
```
>https://www.tutorialkart.com/java/how-to-join-elements-of-string-array-with-delimiter-in-java/

### Find duplicate elements in array
Najprościej zrobić to za pomocą kolekcji [[Set]], która nie może zawierać zduplikowanych elementów
```java
public static boolean noDuplicateLetters(String phrase) {  
    for (String word : phrase.toLowerCase().split(" ")) {  
        Set<Character> duplicationValidationSet = new HashSet<>();  
        for (char letter : word.toCharArray()) {  
            if (!duplicationValidationSet.add(letter)) {  
                return false;  
            }  
        }  
    }  
  
    return true;  
}
```
>https://javarevisited.blogspot.com/2015/06/3-ways-to-find-duplicate-elements-in-array-java.html
>https://edabit.com/challenge/mdJmXLuw8dLxxdGLc

### Copy array by range
```java
char[] censoredStringArray = {'P', '*', 'k', '*', 'm', '*', 'n'};
char[] removedVowelsArray = {'o', 'e', 'o'};

for (int i = 0; i < censoredStringArray.length; i ++) {  
    if (censoredStringArray[i] == '*') {  
        censoredStringArray[i] = removedVowelsArray[0];  
        removedVowelsArray = Arrays.copyOfRange(removedVowelsArray, 1, removedVowelsArray.length);  
    }  
}
```

### Convert char array to String
```java
char[] censoredStringArray = {'P', 'o', 'k', 'e', 'm', 'o', 'n'};

// 1szy sposób
return new String(censoredStringArray);

// 2gi sposób
return String.valueOf(censoredStringArray);
```
>https://www.baeldung.com/java-char-array-to-string

### Sort int array ASC
```java
int[] numbers = {5, 13, 48, 5, 37, 12};
Arrays.sort(numbers);
```
### Sort int array DESC
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

### Concatenate two int arrays
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


### Multi-D array: przemnóż wewn. arraye i zsumuj iloczyny
For instance, `totalVolume([2, 3, 2], [6, 6, 7], [1, 2, 1])` should return `266` since (2 x 3 x 2) + (6 x 6 x 7) + (1 x 2 x 1) = 12 + 252 + 2 = 266
```java
public static int totalVolume(int[][] array) {  
    int total = 0;  
    for (int i = 0; i < array.length; i ++) {  
        int product = 0;  
        for (int j = 0; j < array[i].length; j ++) {  
            if (j != 0) {  
                product *= array[i][j];  
            } else {  
                product = array[i][j];  
            }  
        }  
        total += product;  
    }  
  
    return total;  
}
```

>https://edabit.com/challenge/ibJLbwfkTbP9229Kt