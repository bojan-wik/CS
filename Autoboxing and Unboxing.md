#programming #java

```java
ArrayList<Integer> integerArrayList = new ArrayList<>();  
```

## Autoboxing
Opakowanie [[Primitive Data Types]] w [[Wrapper class]]

```java
for (int i = 1; i <= 5; i ++) {  
    integerArrayList.add(Integer.valueOf(i));
}
```

W tym przypadku `Integer.valueOf(i)` jest przykładem Autoboxingu, czyli:
- bierzemy zmienną `i`, która jest primitive typem `int`
- konwertujemy ją do zmiennej typu `Integer` za pomocą [[Wrapper class]]


## Unboxing
Odpakowanie, wyciąganie [[Primitive Data Types]] z [[Wrapper class]]

```java
for (int i = 1; i <= 5; i ++) {  
    System.out.println("i = " + integerArrayList.get(i).intValue())
}
```

W tym przypadku `integerArrayList.get(i).intValue()` jest przykładem Unboxingu, czyli:
- bierzemy zmienną typu `Integer`, która jest [[Wrapper class]] dla zmiennej typu `int`
- wydobywamy z niej zmienną typu `int`

## Od Java 9  Autoboxing i Unboxing jest zbędny...
...w niektórych przypadkach, ponieważ może być wykonywany automatycznie podczas kompilacji.

Czyli możemy zrobić prościej tak:
```java
Integer myInteger = 56; // autoboxing
int myInt = myInteger;  // unboxing
```
zamiast tak (bo to odbywa się 'w locie' - podczas kompilowania):
```java
Integer myInteger = Integer.valueOf(56);  
int myInt = myInteger.intValue()
```

## Źródła:
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/3561816#overview