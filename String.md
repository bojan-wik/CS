#java #programming 


**String** na podstawowym poziomie stanowi ekwiwalent arraya charów
```java
String name = "Wiktor";

// ekwiwalent

char[] nameLetters = {'W', 'i', 'k', 't', 'o', 'r'};  
String name = new String(nameLetters);
```
## Reverse a String
```java
private static String reverseString(String text) {  
    StringBuilder stringBuilder = new StringBuilder(text);  
    return stringBuilder.reverse().toString();  
}
```

## Add space between each capital letter
```java
private static String addSpaces(String text) {  
    StringBuilder modifiedText = new StringBuilder(text);  
  
    for (int i = 0; i < modifiedText.length(); i ++) {  
        if (i != 0 && Character.isUpperCase(modifiedText.charAt(i))) {  
            modifiedText.insert(i, " ");  
            i ++;  
        }  
    }  
  
    return modifiedText.toString();
}
```
>https://testautomationu.applitools.com/java-programming-course/chapter8b.html

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