
### I. Agata

##### Programowanie: 
- paradygmaty obiektowości -> [[Object-oriented programming]]
- interfejsy vs klasy abstrakcyjne (30) -> [[Interface]], [[Abstract class and method]]
- dziedziczenie vs agregacja vs kompozycja -> [[Inheritance vs Composition vs Aggregation]]
- wyrażenia lambda (14) -> [[Lambda Expressions]]
- typy generyczne -> [[Java Generics]]
- rodzaje kolekcji + różnice (32) -> [[Collections]]
- wzorce projektowe -> [[Design Patterns]]
- serializacja/deserializacja danych 
- jak działają adnotację i jak stworzyć własną 
 
##### Maven/junit/testng: -> [[JUnit]] [[TestNG]]
- czym jest pom.xml
- install vs build vs test vs clean 
- adnotacje + przykłady użycia 
- sposoby parametryzacj testów 

##### Selenium 
- Implicitly vs explicit wait vs fluent wait  -> [[Selenium Waits]]
- Xpath I css -> [[locators - selectors]]
- Page object patter (z odmianą fluent)  
- Page factory  
- Selenium grid  
- StaleElementReferenceException  
- Czym jest obiekt DOM  
- Klasy actions I jsexecutor  
- Jakieś ogólne pytania odnośnie projektowanie frameworka czy bibliotek odpowiedzialnych za tworzenie raportów  
- W jaki sposób spiąc testy w narzędziu CI -> [[Jenkins]] 
- Czasami rzeczy z BDD cucumber jeżeli są wymagane do projektu  -> [[Cucumber]]

##### API -> [[REST API]]
- rest vs soap 
- czym jest plik wsdl  -> [[WSDL]]
- czym jest endpoint 
- rodzaje zapytań http 
- tworzenie zapytań w rest assured -> [[REST Assured]]

##### SQL -> [[SQL]]
- having vs where 
- podzapytania 
- różne joiny 

> [08:53] MT
to tak mniej więcej co jest na rozmowach 
[08:53] MT  
oczywiście nie zawsze pytam wszystko tylko wybieram, 
[08:53] MT  
no i do tego dochodzą czasami specyfine pytania z technologii z CV kandydata czy wymaganych pod projekt

### II. Adam
![[Pasted image 20220309142509.png]]
* static -> [[static vs instance]]
* Zadanie z rekurencji -> [[Recursion]]

### III. Paweł B.
1. https://www.jdoodle.com/ia/c9N - zmodyfikować klasy w taki sposób aby nie pojawiay się błędy - OK
2. co to jest polimorfizm -> [[Polymorphism]]
3. co to jest dziedziczenie -> [[Inheritance]]
4. co to jest hermetyzacja / enkapsulacja -> [[Encapsulation]]
5. co to jest abstrakcja, w jakich sytuacjach używać
6. czym różni się maven od gradle
7. do czego służy garbage collector -> [[Garbage Collector]]
8. rodzaje kolekcji i kilka słów o każdym z nich -> [[Collections]]
9. zadanie: są 2 duże zbiory danych (każdy ok 100 000 rekordów) i w jaki sposób określić, że wszystkie elementy ze zbioru 1 są zawarte w zbiorze 2
10. jakie są rodzaje selektorów i których najczęściej używasz -> [[locators - selectors]]
11. rodzaje wait'ów w selenium i czym się różnią -> [[Selenium Waits]]
12. zadanie: na stronie http://automationpractice.com/ dodać produkt do kosza, przejść do kosza i odczytać cenę (bez waluty) - napisać na to lokator
13. jak zorganizować w projekcie stronę, która ma dużo elementów / sekcji
14. do czego służy jenkins
15. jakie znasz komendy gita
16. zadanie: podać kolejne komendy gita dla scenariusza - utwórz projekt --> git --> wprowadź zmiany --> git
17. napisać proste zapytanie sql, co to są left/right join, order by,  group by, count itp 
18. metody http
19. co oznaczają grupy kodów http 100/200/300/400/500 
20. komendy linuxa

### IV. Bank

#### Dominik

###### 1. Co to jest klasa? Co to jest obiekt?

a) klasa:
		- kod który stanowi wzorzec/blueprint dla przyszłych obiektów
		- zawiera zarówno fieldy, jak i metody
		- zawiera konstruktor
	
b) obiekt:
		- instancja/reprezentacja klasy
		- przechowuje informacje o zmiennych, pozwala się do nich odwoływać
		- za jego pomocą możemy wywoływać metody

###### 2. Z jakich wzorcow korzystałeś przy pisaniu testow automatycznych?
* page object model
* page factory? - klasy, których metody przygotowywały obiekty webdrivery pod poszczególne przeglądarki?

###### 3. W jaki sposob w java zaimplementowac hermetyzację (enkapsulację)? Gdy w bashu tworzymy obiekt.

###### 4. Jakbyś opisał typy proste, co to jest (vs typy bardziej złożone)?

a) typy proste (primitive)
		- typy wbudowanie, w Javie jest ich 8 np. int, boolean, char etc.
		- elementy budujące, z których składają się typy złożone
		- zmienne typów prostych przechowują w pamięci konkretne wartości
		
b) typy złożone (reference)
		- typy zdefiniowane w standardowych bibliotekach Java (np. String, tablice)
		- albo tworzone przez programistów poprzez pisanie klas
		- zmienne typów złożonych przechowują adresy (referencje do) obiektów w pamięci

###### 5. Przeciążanie metod w java. Jesli chcemy mieć dwie metody o tej samej nazwie - jakie powinny mieć różnice?

###### 6. Czy korzystasz w metodzie w integerów? W jaki sposób byś utworzył big decimala? Jakie są na to sposoby, jakie różnice?

Klasy (z java.math) do przechowywania ogromnych liczb, mają dodatkowe funkcje mat. nadające się do precyzyjnych obliczeń np. w bankowości

a) BigInteger - klasa dla wielkich liczb całkowitych
	
b) BigDecimal - klasa dla wielkich floatów. Tworzenie:
	
* String jako argument - możliwość podania wartości przekraczających zakres typu double
```java
BigDecimal bigDecimal1 = new BigDecimal("0.5");
```
* metoda valueOf - trzeba trzymać się zakresu typów double
```java
BigDecimal bigDecimal2 = BigDecimal.valueOf(0.55555);
```
		
https://javastart.pl/baza-wiedzy/java-podstawy-jezyka/funkcje-matematyczne-i-wielkie-liczby

###### 7. Czy wiesz co to jest string pool, integer pool. Jak byś łączył stringi?

a) string pool:
* miejsce w pamięci, do którego trafiają obiekty typu String NIE utworzone za pomocą operatora new np. `String name = "Wiktor";`
* dzięki niemu wiele obiektów String o tej samej wartości wskazują na ten sam adres w pamięci
* optymalizacja pamięci JVM, przyspiesza porównywanie Stringów
		
b) integer pool
* cachowanie często używanych obiektów Integer
* poprawa wydajności podczas procesowania Integerów np. podczas autoboxingu - 	`Integer.valueOf(int)` provides better performance than `new Integer(int)`

c) łączenie Stringów
* metoda concat()
* +

https://1024kb.pl/rekrutacja/string-pool/
https://dharashahkenya.wordpress.com/2019/02/06/string-pool-and-integer-pool/

###### 8. Testy automatyczne GUI. Fluent (wait?) w Selenium - czym sie charakteryzuje, jakie ma zalety?

###### 9. CSS Selectory i XPath - najmocniejsze i najsłabsze strony

###### 10. Jak sie dostac za pomocą Selectora lub Xpatha do zaznaczonego elementu, ew. jak sie dostac bez IDka?

```java
//A[@id = '8']
//Records/A[8]
	
#8
Records:nth-child(8)
```

###### 11. Java wyjatki - po co stosujemy try catch?

###### 12. Postman do testowania API i SoapUI? - jakie są różnice? Jak są tam przekazywane/dostarczane dane?

a) SoapUI
	- testowanie wielu API protokołów m.in: Soap, Rest, 
	- tylko XML
	- wspiera data-driven testing (z zewn. plików)
	- groovy

b) Postman
	- testowanie tylko Rest API
	- wiele formatów, m.in.: XML, JSON, text, HTML
	- javascript
	- współpraca z innymi



###### 13. xml i json - moga byc wykorzystane w Postmanie. Jaka jest różnica pomiedzy xml i json?

a) XML
		- bardziej bezpieczny
		- struktura tagów
		- ma namespace
		- ma komentarze
		- różne enkodowania
	
b) JSON
		- bazuje na JavaScript
		- łatwiejszy do odczytu niż XML + lekki/szybszy?
		- wspiera arraye
		- tylko enkodowanie UTF-8

###### 14. Metody get put post delete patch - co do czego służy?

###### 15. Kody odpowiedzi, np. 200, 500, 400, 401, 403 - co oznaczają?

2xx powodzenie
	200 ok
	201 created

3xx przekierowania

4xx błędy po stronie klienta (np. przeglądarki)
	400 bad request np. błędna składnia requesta
	401 unauthorized - wymaga uwierzytelnienia
	403 forbidden - request jest ok, ale dostęp jest zabroniony
	404 not found

5xx błędy po stronie serwera
	500 internal server error
	503 service unavailable np. przez przeciążenie
	504 gateway timeout

###### 16. Bazy danych - roznica między inner join a left right join?

inner join - zwraca rekordy, które mają pasujące rekordy w obu tabelach

LEFT JOIN - zwraca wszystkie rekordy z lewej tabeli i dopasowane rekordy z prawej tabeli

RIGHT JOIN - zwraca wszystkie rekordy z prawej tabeli i dopasowane rekordy z lewej tabeli

FULL JOIN - zwraca wszystkie rekordy, niezależnie od tego, czy pasujący rekord istnieje w drugiej tabeli.

###### 17. Indexy w SQL - po co są?
	
* specjalne tabele używane do przyspieszenia wyszukiwania danych
* odwołania do danych w tabeli
* coś jak spis treści w książce
* niedostępne dla zwykłych userów

###### 18. Jak najprościej posortować wyniki w SQL?

order by

###### 19. Czy korzystales z GIT'a do kontroli wersji? Co zrobic, zeby przeniesc cos ze swojej gałązki na gałązkę mastera?

###### 20. Czy prowadziłeś testy wydajnościowe? Z jakim narzędziem?

###### 21. Czy robiłeś testy manualne?

#### Ja

Co to jest Super i this
Co to jest konstruktor?
Co to jest Final?
Jaka jest różnica między klasą, a interface'm?
Kluczowa zaleta XPath vs CSS Selectorów. Do czego służy kropka w XPath?
Dlaczego warto stosowac Fluenwait'y w Selenium?
W przypadku testow API mamy kilka metod (np. HTTP). Którą metodę bys wykorzystal dla zwrocenia obiektu?
Gdybys testowal API korzystające z metody POST, a otrzymał obiekt, to co bys sobie pomyslal?
Jaka jest różnica między PUTem a PATCHem?