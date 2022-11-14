#java 

```java
Set<String> fruits = new HashSet<>();
```

Dodawanie elementów
```java
fruits.add("apple");  
fruits.add("banana");  
fruits.add("lemon");  
fruits.add("orange");
```

Usuwanie elementów
```java
fruits.remove("lemon");
```

Sprawdzenie, czy dany element istnieje
```java
System.out.println(fruits.contains("kiwi"));
```

Sprawdzenie rozmiaru kolekcji
```java
System.out.println(fruits.size());
```

Loopowanie po elementach
```java
// looping - iterator  
  
Iterator<String> i = fruits.iterator();  
while (i.hasNext()) {  
    System.out.println(i.next());  
}  
  
// looping - for each loop  
  
for (String fruit : fruits) {  
    System.out.println(fruit);  
}  
  
// looping - forEach()
  
fruits.forEach(fruit -> System.out.println(fruit));
```