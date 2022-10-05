# Scanner class
#java #programming 

Klasa w Javie słuząca do zczytywania inputu od usera.

**Przykład użycia:**
Zczytanie od usera liczb i znalezienie pośród nich najmniejszej liczby.

```java
public class Main {

    private static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        int[] enteredNumbers = readIntegers(readCount());
        int minNumber = findMin(enteredNumbers);

        System.out.println("\nEntered numbers: " + Arrays.toString(enteredNumbers));
        System.out.println("Smallest number: " + minNumber);
    }

    private static int readCount() {
        System.out.println("Enter count: ");
        return scanner.nextInt();
    }

    private static int[] readIntegers(int count) {
        int[] array = new int[count];
        System.out.println("Enter " + count + " numbers: ");
        int i = 0;
        while (i < array.length) {
            array[i] = scanner.nextInt();
            i ++;
        }

        return array;
    }

    private static int findMin(int[] array) {
        int minNumber = array[0];
        for (int i = 1; i < array.length; i ++) {
            if (array[i] < minNumber) {
                minNumber = array[i];
            }
        }

        return minNumber;
    }
}
```