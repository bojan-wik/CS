# Locators, selectors
#selenium

Nazwy locators i selectors oznaczają to samo i są wykorzystywane zamiennie.

## 1. Typy locatorów
* ID
* class name
* tag name
* link text
* XPath
* CSS selector

## 2. Ogólne tipsy
a) Nie wszystkie elementy mają ID/className/name – dlatego Xpath/CSS selector jest generalnie preferowany

b) Jeżeli nazwa locatora jest:
* alphanumeryczna (np. *id="u_0_2"*) - lepiej nie używać go w testach, bo może się ona zmieniać przy przeładowywaniu strony.
* oparta o tekst – lepiej nie używać, bo ten tekst może się zmieniać np. Button z tekstem 'add to cart', który po kliknięciu zmienia tekst na 'added'

c) Jeżeli na stronie jest kilka elementów z tą samą nazwą locatora (np. *class="is_required"*) to brany jest pod uwagę ten element, który pierwszy występuje w DOMie (od góry).

d) Możliwe jest tylko wyszukiwanie po jednej nazwie klasy (np. *class="is_required"*). Użycie więcej niż jednej klasy (np. *class="is_required validate account_input form-control"*) wywali błąd. 

e) Locator Xpath może być zdefiniowany na wiele różnych sposobów. Raczej unikać używania absolutnego Xpath (zaczynającego się od "/html...") - może być niestabilny.

## 3. XPath
### a) syntax
```
//tagName[@attribute='value'] 
//*[@attribute='value']
```

### b) absolute vs relative Xpath

Relative path - ścieżka w której odnoszę się bezpośrednio do danego node, bez podawania relacji do jego parenta itp. np.
```
//input[@id='search_query_top']
```

Absolute path - ścieżka w której podaję w jakiej relacji jest dany node np. 
```
/html/body/div/div[1]/header/div[3]/div/div/div[2]/form/input[4]
```

### c) parent-child relationship
* metoda, ktróra sprawdza się w przypadku kiedy nie mamy na stronie żadnych elementów, które są albo unikalne, albo statyczne - wtedy opcją jest napisanie xpath właśnie w oparciu o relację parent-child poszczególnych elementów na stronie 
* wychodzę od zdefiniowania xpath dla parent-elementu I później schodzę po elementach w dół do child-elementu
* mając taki webelement (zaznaczony na zielono) 

![[Pasted image 20220217092213.png]]

xpath dla niego wyglądałby tak:
```
//div[@jsmodel='vWNDde']/div[@jsmodel='QubRsd']/div[@jsname='RNNXgb']/div[@class='SDkEP']/div[@jsname='gLFyf']/input[@name='q'] 
```

* aczkolwiek w sytuacji kiedy dany element nie ma żadnych sibilingów z tym samym tagname, nie trzeba definiować jego atrybutów I też zadziała np.
```
//div[@jsmodel='vWNDde']/div[@jsname='RNNXgb']/div[@jsname='gLFyf']/input[@name='q']
```

* mogę też używać indeksów, zamiast podawać nazwy atrybutów poszczególnych tagname
```
//div[@jsmodel='vWNDde']/div/div[1]/div/div[2]/input
```


### d) identyfikowanie siblingów
czyli "braci" i "sióstr" danego node

* following sibiling np.
```
//div[@id='search_block_top']/following-sibling::div
```

* preceding sibiling np.
```
//div[@id='search_block_top']/preceding-sibling::div
```
Takie przechodzenie do tyłu jest możliwe tylko z xPath, nie jest możliwe z CSS selectors


### e) regular expressions

| expression | syntax | example |
| ----------- | ----------- | ----------- |
| contains | //tagName[contains(@attribute, 'value')] | //input[contains(@id, 'user-')] |
| starts with | //tagName[starts-with(@attribute, 'value')] | //input[starts-with(@name, 'pass')] |
| ends with | //tagName[ends-with(@attribute, 'value')] | //input[ends-with(@id, 'button')] |

ends with nie działało mi z xpath, tylko z css selector

---
* https://www.red-gate.com/simple-talk/wp-content/uploads/imported/1269-Locators_table_1_0_2.pdf?file=4937
* https://exadel.com/news/how-to-choose-selectors-for-automation-to-make-your-life-a-whole-lot-easier