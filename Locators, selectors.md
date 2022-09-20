# Locators, selectors
#selenium

Nazwy locators i selectors oznaczają to samo i są wykorzystywane zamiennie.

## Typy locatorów
* ID
* class name
* tag/element name
* link text
* XPath
* CSS selector

## Ogólne tipsy

```html
<button class="btn btn-info" id="submit" name="submit">Button</button>
```

1. W pierwszej kolejności starać się pisać lokatory w oparciu o ID, atrybut name, class name:

-  **ID** powinien być unikalny na stronie. Jeżeli dany element ma ID to brać go w pierwszej kolejności. W tym przypadku: `By.id("submit")`

- **Atrybut name** jest używany w elementach typu `<input>` np. input, button, text area. Ten atrybut powinien być unikalny, więc można z niego korzystać na równi z ID. W tym przypadku: `By.name("submit")`

- **Class name** służy do stylowania elementów i najczęściej jest współdzielony przez wiele elementów, więc jeżeli chcemy znaleźć listę konkretnych elementów, to Class name może być dobrym wyborem. W tym przypadku: `By.className("btn-info")`

2. W drugiej kolejności pisać lokatory w oparciu o Xpath albo CSS selector:




## CSS Selectors

class name
```css
tagName.className
```

id
```css
#id
```

pośredni child
```css
selector selector
```
np.
```css
div.et_pb_newsletter_form input.input
```

bezpośredni child
```css
selector > selector
```
np.
```css
p.et_pb_contact_form_field > input.input
```

OR
```css
selector, selector
```
np.
```css
ol > li, ul > li
```

szukanie po nazwach atrybutów
```css
tagName[attributeName]
```
np.
```css
div[style]
```

szukanie po nazwach atrybutów i po ich wartościach (equals)
```css
tagName[attributeName='value']
```
np.
```css
a[data-zci-link='images']
```

szukanie po nazwach atrybutów i po ich wartościach (contains)
```css
tagName[attributName*='value']
```

NOT - zwróć elementy, które nie zawierają...
```css
locator:not(locator)
```
np.
```css
ol.related-searches__list:not(.related-searches__list--first)
```

szukanie po indeksach elementów:
```css
locator:nth-child(n)
```

np.
```css
div.nrn-react-div:nth-child(3)
```

CSS selector nie może:
- jednoznacznie zidentyfikować dowolnego webelementu
- wyszukiwać po tekście webelementu
- traversować po poprzedzających siblingach





a) Nie wszystkie elementy mają ID/className/name – dlatego Xpath/CSS selector jest generalnie preferowany

b) Jeżeli nazwa locatora jest:
* alphanumeryczna (np. *id="u_0_2"*) - lepiej nie używać go w testach, bo może się ona zmieniać przy przeładowywaniu strony.
* oparta o tekst – lepiej nie używać, bo ten tekst może się zmieniać np. Button z tekstem 'add to cart', który po kliknięciu zmienia tekst na 'added'

c) Jeżeli na stronie jest kilka elementów z tą samą nazwą locatora (np. *class="is_required"*) to brany jest pod uwagę ten element, który pierwszy występuje w DOMie (od góry).

d) Możliwe jest tylko wyszukiwanie po jednej nazwie klasy (np. *class="is_required"*). Użycie więcej niż jednej klasy (np. *class="is_required validate account_input form-control"*) wywali błąd. 

e) Locator Xpath może być zdefiniowany na wiele różnych sposobów. Raczej unikać używania absolutnego Xpath (zaczynającego się od "/html...") - może być niestabilny.

## 3. XPath
### a) syntax
```properties
//tagName[@attribute='value'] 
//*[@attribute='value']
```

### b) absolute vs relative Xpath

Relative path - ścieżka w której odnoszę się bezpośrednio do danego node, bez podawania relacji do jego parenta itp. np.
```
//input[@id='search_query_top']
```

Absolute path - ścieżka w której podaję w jakiej relacji jest dany node np. 
```properties
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

* parent np.
```
//input[@id = 'text']//parent::span
```


### d) identyfikowanie siblingów
czyli "braci" i "sióstr" danego node

* następujący sibiling np.
```
//div[@id='search_block_top']/following-sibling::div
```

* poprzedzający sibiling np.
```
//div[@id='search_block_top']/preceding-sibling::div
```
Takie przechodzenie do tyłu jest możliwe tylko z xPath, nie jest możliwe z CSS selectors


### e) regular expressions

| expression | syntax | example |
| ----------- | ----------- | ----------- |
| contains | //tagName[contains(@attribute, 'value')] | //span[contains(text(),'Add section')] //div[contains(@class, 'mm-document-tile-grid-title')]|
| starts with | //tagName[starts-with(@attribute, 'value')] | //input[starts-with(@name, 'pass')] |
| ends with | //tagName[ends-with(@attribute, 'value')] | //input[ends-with(@id, 'button')] |

ends with nie działało mi z xpath, tylko z css selector

---
* https://www.red-gate.com/simple-talk/wp-content/uploads/imported/1269-Locators_table_1_0_2.pdf?file=4937
* https://exadel.com/news/how-to-choose-selectors-for-automation-to-make-your-life-a-whole-lot-easier