# Stream API
#java 

* feature wprowadzony wraz z Java 8
* upraszcza kod
* wykorzystuje/wspiera założenia [[Functional programming]]

## Główne założenia:

* Streamy same w sobie nie są [[data structure]] - nie przechowują danych. Przyjmują tylko jako input różne typy kolekcji danych np. [[Collections]], [[Array]] itp.
* Taki przyjęty przez stream input stanowi jego sekwencję elementów na których potem można wykonywać różne operacje, które potem można pipelinować, żeby otrzymać oczekiwany efekt
* Streamy nie modyfikują oryginalnego źródła danych (przyjętego jako input)

## Sposób działania
można podzielić na 3 etapy:
1. Uworzenie streama - przekonwertowanie inputu do streama
2. Zastosowanie *operacji pośrednich* ([[map()]], [[filter()]] albo [[sorted()]])
3. Zastosowanie *operacji kończącej* (np. [[forEach()]], [[count()]], [[collect()]], [[reduce()]])

## Zastosowanie
na przykładzie zadania:
> Policz ile w danej liście jest imion zaczynających się od litery 'A'

Mając taką listę
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
long countNamesStartingWithA = namesList.stream().filter(name -> name.startsWith("A")).count();
```

#### string array -> stream -> string array
```java
String[] array = {"Arizona", "CA", "NY", "Nevada"};
Stream<String> streamArray = Arrays.stream(array);

String[] filteredArray = streamArray.filter(element -> element.length() <= 2).toArray(String[]::new);

```

---
* https://github.com/bojan-wik/SeleniumWithJavaCourse/tree/master/src/Chapter14_JavaStreams
* https://geek.justjoin.it/zastosowanie-stream-api-z-java-8-przyklady
* https://www.geeksforgeeks.org/stream-in-java/