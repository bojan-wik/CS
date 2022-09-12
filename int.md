# int
#java #programming 

## Extract last two digits and last digit of int
```java
int number = 125;
int lastTwoDigits = number % 100; // 25
int lastDigit = number % 10; // 5
```

### Drop last digit from int
```java
int number = 125;
int numberWithoutLastDigit = number / 10; // 12
```

##### Przykład użycia: sumowanie cyfr w liczbie
```java
public static int sumDigits(int number) {  
    if (number < 10) {  
        return -1;  
    }  
    int sum = 0;  
    while (number > 0) {  
        sum += number % 10;  
        number /= 10;  
    }  
    return sum;  
}
```