# Selenium methods
#selenium 

#### getText()
Wyciąganie tekstu z webelementu, ale działa tylko z webelementami, które nie są ukryte.
Dla ukrytych webelementów muszę użyć `getAttribute("textContent")` np.
```java
assertThat(driver.findElement(By.xpath("//span[@ng-if='!isCustomCaption']")).getAttribute("textContent")).contains("0 file");
```
>https://stackoverflow.com/a/32475546

#### isSelected()
Sprawdza, czy webelement jest selected, czy nie. Działa na radio button, checkbox, opcjach w menu.

Jeżeli chodzi o radio button, to działa chyba tylko na klasycznych, HTMLowych `<input type="radio">`
bo np. na Angularowym `md-radio-button` już nie działa - zwraca zawsze false.
W tym przypadku robiłem asercję po jakimś atrybucie np.
```java
assertThat(radioButtonGraphicalLogo.getAttribute("aria-checked")).isEqualTo("true");
```