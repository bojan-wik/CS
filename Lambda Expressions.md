#programming #java 

## Definicja

Lambdy pozwalają na pisanie kodu w sposób funkcyjny. Sama Java jest językiem obiektowym. Odnosząc lambdy do programowania obiektowego, można o nich myśleć jak o klasach tymczasowych (anonymous [[Inner Class]]) zawierających tylko jedną metodę.

## Przykład

Posortować imiona alfabetycznie (ASC)

```java
List<String> names = Arrays.asList("Kasia", "Leon", "Anna", "Wiktor");

// WITHOUT lambda expressions

Collections.sort(names, new Comparator<String>() {  
    @Override  
    public int compare(String name1, String name2) {  
        return name1.compareToIgnoreCase(name2);  
    }  
});

// WITH lambda expressions

Collections.sort(names, (name1, name2) -> name1.compareToIgnoreCase(name2));
```

## Składnia

![[Pasted image 20221125114414.png]]

## Źródła:
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/5653618#notes
- https://javastart.pl/baza-wiedzy/slownik/wyrazenia-lambda