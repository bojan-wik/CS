#java 

#### Abstraction
process of hiding the implementation details from the user, only the functionality will be provided to the user. The user will have the information on what the object does instead of how it does it. 

 
#### Abstract Class: 
- Declared with the abstract keyword 
- Może zawierać zarówno non-abstract methods (z implementacją, body/kodem), jak i abstract methods 
- Abstract classes (w odróżnieniu od Interfases) nie osiągają 100% poziomu abstrakcji, tylko częściowy 
- Nie można tworzyć obiektów Abstract class - Abstract class cannot be instantiate 


#### Przykład:
- Istnieje Parent Class, która definiuje zasady/metody budowania samolotów. Prawie wszystkie te metody są zaimplementowane (mają body/kod) 
- Parent Class ma pod sobą różne Child Classes, które odpowiadają firmom tworzącym samoloty. Child Classes/firmy muszą odziedziczyć zasady/metody budowania samolotów i zaaplikować je do własnych konstrukcji. 
- Ale jest jedna metoda w Parent Class, która nie jest zaimplementowana (nie ma body/kodu), czyli nie narzuca żadnej implementacji i każda z Child Classes może ją sobie zaimplementować indywidualnie np. Metoda dotycząca koloru samolotu, który może być dobrany dowolnie przez każdą z firm 
- Taka metoda bez implementacji to Abstract Method 
- Jeżeli w danej class jest chociaż jedna Abstract Method to wtedy class staje się Abstract Class 

#### Interface vs. Abstract Class – differences:

|     |                                  | Interface                     | Abstract Class                                 |
| --- | -------------------------------- | ----------------------------- | ---------------------------------------------- |
| 1   | Can contain...                   | only abstract methods         | abstract methods, non-abstract methods or both |
| 2   | Access specifiers for methods... | must be public                | Can have any access specifier, except private  |
| 3   | Variables defined...             | must be public, static, final | can have any access specifiers, except private |
| 4   | To implement we use...           | 'implement' keyword           | 'extends' keyword                                                |

---
- https://github.com/bojan-wik/SeleniumWithJavaCourse/tree/master/src/Chapter30_CoreJava1