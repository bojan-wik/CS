# Autoboxing and Unboxing
#java 

```java
ArrayList<Integer> integerArrayList = new ArrayList<>();  
```

Autoboxing
```java
for (int i = 1; i <= 5; i ++) {  
    integerArrayList.add(Integer.valueOf(i));
}
```

Unboxing
```java
for (int i = 1; i <= 5; i ++) {  
    System.out.println("i = " + integerArrayList.get(i).intValue())
}
```

Deprecated from Java 9