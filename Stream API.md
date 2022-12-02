#programming #java 

* feature wprowadzony wraz z Java 8
* upraszcza kod
* wykorzystuje [[Lambda Expressions]]
* wykorzystuje/wspiera założenia [[Functional programming]]

## Główne założenia:

* Streamy same w sobie nie są [[data structure]] - nie przechowują danych. Przyjmują tylko jako input różne typy kolekcji danych np. [[Collections]], [[Array]] itp.
* Taki przyjęty przez stream input stanowi jego sekwencję elementów na których potem można wykonywać różne operacje, które potem można pipelinować, żeby otrzymać oczekiwany efekt
* Streamy nie modyfikują oryginalnego źródła danych (przyjętego jako input)

## Sposób działania
można podzielić na 3 etapy:
1. Uworzenie streama - przekonwertowanie inputu do streama
2. Zastosowanie *operacji pośrednich* ([[map()]], [[filter()]] albo [[sorted()]]), które dalej zwracają stream
3. Zastosowanie *operacji kończącej* (np. [[forEach()]], [[count()]], [[collect()]], [[reduce()]]), które zwracają void albo obiekt, który nie jest już streamem

## Zastosowanie
na przykładzie zadania:
> Policz ile w danej liście jest imion zaczynających się od litery 'A'

Mając taką listę:
```Java
static List<String> namesList = Arrays.asList("Wiktor", "Adam", "Robert", "Aleks", "Arab");
```

Rozwiązanie bez użycia stream
```Java
int countNamesStartingWithA = 0;
        for (int i = 0; i < namesList.size(); i += 1) {
            String name = namesList.get(i);
            if (name.startsWith("A")) {
                countNamesStartingWithA += 1;
            }
        }
        System.out.println(countNamesStartingWithA);
```

Rozwiązanie z użyciem stream
```Java
long countNamesStartingWithA = namesList.stream()
	.filter(name -> name.startsWith("A"))
	.count();
```

## Metody

Mając takie streamy:
```java
Stream<String> ioNUmberStream = Stream.of("I26", "I17", "I29", "071");  
Stream<String> inNumberStream = Stream.of("N40", "N36", "I26", "I17", "I29", "071");
```

#### concat()
połączenie kilku streamów w jeden
```java
Stream<String> concatStream = Stream.concat(ioNUmberStream, inNumberStream);
```

#### Remove duplicates + peek 
(podejrzenie, trochę jak print) + count
```java
System.out.println(concatStream  
        .distinct()  
        .peek(System.out::println)  
        .count());
```

#### collect()
pozwala na przypisanie outputu z chaina do osobnej:

##### listy
```java
List<String> iNumbersSorted = concatStream  
        .filter(number -> number.startsWith("I"))  
        .distinct()  
        .sorted().  
        collect(Collectors.toList());

// [I17, I26, I29]
```

##### mapy
```java
Map<Character, List<String>> numbersGroupedByLetter = concatStream  
        .distinct()  
        .collect(Collectors.groupingBy(number -> number.charAt(0)));

// {0=[071], I=[I26, I17, I29], N=[N40, N36]}
```

#### flatMap()
pozwala na "spłaszczenie" multidimensional arrays do jednego poziomu

>https://github.com/bojan-wik/UdemyJavaMasterclass/tree/master/src/section16/streams/flatmap

## Code snippets

#### string array -> stream -> string array
```java
String[] array = {"Arizona", "CA", "NY", "Nevada"};
Stream<String> streamArray = Arrays.stream(array);

String[] filteredArray = streamArray.filter(element -> element.length() <= 2).toArray(String[]::new);

```

## Źródła:
* https://github.com/bojan-wik/SeleniumWithJavaCourse/tree/master/src/Chapter14_JavaStreams
* https://geek.justjoin.it/zastosowanie-stream-api-z-java-8-przyklady
* https://www.geeksforgeeks.org/stream-in-java/
* https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/5723588#notes