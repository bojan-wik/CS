# String
#java #programming 

## Iterate over String
```java
String censoredString = "P*k*m*n";

for (char symbol : censoredString.toCharArray()) {  
    System.out.println(symbol);
    }  
}
```
>https://www.geeksforgeeks.org/iterate-over-the-characters-of-a-string-in-java/

## Extract digit from a String and convert it to int
```java
String str = "The price of the book is $49";
String numberOnly = str.replaceAll("[^0-9]", "");
int numberOnlyInt = Integer.parseInt(numberOnly);
```

## Convert `String` to:
### `double`
```java
String numberAsString = "69.125";
double number = Double.parseDouble(numberAsString);
```

### `int`
```java
String numberAsString = "5";
int number = Integer.parseInt(numberAsString);
```