
#java #programming 

## I. for & for-each loops

### 1. for loop
- używamy kiedy wiemy dokładnie ile ma być iteracji (count-controlled)
- zmienna counter/sentinel definiowana wewn. pętli
- zalecana do używania kiedy wiemy dokładnie ile ma być iteracji

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

### 2. for-each loop
- używamy kiedy wiemy dokładnie ile ma być iteracji (count-controlled)
- bez zmiennej counter/sentinel przez co ma swoje ograniczenia
- bardziej czytelna niż zwykła for loop
- zalecana do używania kiedy wiemy dokładnie ile ma być iteracji
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

## II. while and do-while loops

### 1. while loop
- używamy, kiedy nie wiemy dokładnie ile ma być iteracji, tylko że pętla ma działać dopóki jakiś warunek jest spełniony (condition-controlled)
- zmienna counter/sentinel definiowana własnoręcznie poza pętlą
- warunek testujemy na początku pętli.
- zalecana do używania w sytuacji kiedy pętla może, ale nie musi być odpalana
```java
int count = 1;
while(count != 6) {
	System.out.println("Count value is " + count);
	count ++;
}
```

### 2. do-while loop
- tak jak w przypadku while loop - pętla działa dopóki jakiś warunek jest spełniony (condition-controlled)
- zmienna counter/sentinel definiowana własnoręcznie poza pętlą
- warunek testujemy na końcu pętli - kod uruchimi się przynajmniej raz
- zalecana do używania w sytuacji, kiedy pętla ma być odpalona przynajmniej raz
```java
int count = 1;
do {
    System.out.println("Count value was " + count);
    count ++;
} while(count != 6);
```

Zarówno w przypadku pętli *for* jak i *while* możemy używać [[break and continue statemets]]