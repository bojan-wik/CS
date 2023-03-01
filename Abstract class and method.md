#java 

## Abstraction
Jeden z paradygmatów programowania obiektowego [[Object-oriented programming]].

Process of hiding the implementation details from the user, only the functionality will be provided to the user. The user will have the information on what the object does instead of how it does it.

## Keyword `abstract`:
- non-access modifier
- możliwy do użycia przy klasach i metodach
- używany gdy chcemy zdefiniować swego rodzaju szablon dla klasy lub metody, np.
```java
public abstract class Shape {
	
	public abstract double calculateArea();
}
```

## Abstract method
to metoda bez implementacji/body, tylko z samą sygnaturą

## Abstract class
- może zawierać zarówno standardowe metody (z implementacją/body) jak metody abstrakcyjne
- z racji tego klasa abstrakcyjna (w odróżnieniu od [[Interface]]) nie może osiągnąć 100% poziomu abstrakcji, tylko częściowy 
- nie można tworzyć obiektów klasy abstrakcyjnej (cannot be instantiate), 
- ale można po niej dziedziczyć - wtedy sub-klasa jest odpowiedzialna za zaimplementowanie wszystkich metod abstrakcyjnych z super-klasy,
- gdy taka sub-klasa potrzebuje zaimplementować tylko część metod abstrakcyjnych - sama też musi zostać zadeklarowana jako klasa abstrakcyjna

**Przykład (kurs z O'Reilly):**
- Istnieje Parent Class, która definiuje zasady/metody budowania samolotów. Prawie wszystkie te metody są zaimplementowane (mają body/kod) 
- Parent Class ma pod sobą różne Child Classes, które odpowiadają firmom tworzącym samoloty. Child Classes/firmy muszą odziedziczyć zasady/metody budowania samolotów i zaaplikować je do własnych konstrukcji. 
- Ale jest jedna metoda w Parent Class, która nie jest zaimplementowana (nie ma body/kodu), czyli nie narzuca żadnej implementacji i każda z Child Classes może ją sobie zaimplementować indywidualnie np. Metoda dotycząca koloru samolotu, który może być dobrany dowolnie przez każdą z firm 
- Taka metoda bez implementacji to Abstract Method 
- Jeżeli w danej class jest chociaż jedna Abstract Method to wtedy class staje się Abstract Class 

### Interface vs. Abstract Class:

|     |                                  | Interface                     | Abstract Class                                 |
| --- | -------------------------------- | ----------------------------- | ---------------------------------------------- |
| 1   | Can contain...                   | only abstract methods         | abstract methods, non-abstract methods or both |
| 2   | Access specifiers for methods... | must be public                | Can have any access specifier, except private  |
| 3   | Variables defined...             | must be public, static, final | can have any access specifiers, except private |
| 4   | To implement we use...           | 'implement' keyword           | 'extends' keyword                                                |

## Źródła:
- https://github.com/bojan-wik/SeleniumWithJavaCourse/tree/master/src/Chapter30_CoreJava1
- https://testautomationu.applitools.com/java-programming-course/chapter11a.html