# break and continue statemets
#java 

## break
//tbd
## continue
Jeżeli warunek == true to statement *continue* powoduje, że kod za nim nie zostanie już wyegzekwowany (print w tym przypadku) tylko powróci do początku pętli *while* 
```java
int number = 0;  
  
while (number <= 10) {  
    number ++;  
    if (!isEvenNumber(number)) {  
        continue;  
    }  
    System.out.println("Even number: " + number);  
}
```