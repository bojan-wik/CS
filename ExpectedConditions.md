#selenium 

#### titleContains
Czy tytuł strony **zawiera konkretny string** np.
```java
webDriverWait.until(ExpectedConditions.titleContains("giant panda"));
```
Tytuł strony to to co znajduje się na tabie w przeglądarce albo w elemencie `<title>` w DOMie

#### attributeToBe / attributeContains
Czy webelement->atrybut->wartość ***to konkretny string*** np.
```java
webDriverWait.until(ExpectedConditions.attributeToBe(tabGroupDetails, "aria-selected", "true"));
```

Czy webelement->atrybut->wartość ***zawiera konkretny string*** np.
```java
webDriverWait.until(ExpectedConditions.attributeContains(By.xpath(SECTION_TAG_PREVIEW_CONTENT_XPATH), "style", "rgb(109, 139, 184)"));
```

Powyższe metody nie działają w przypadku kiedy dany webelement->atrybut->wartość to pusty string np.
```html
<select id="dropdown" multiple="">
```
wtedy użyłem takiego workarounda
```java
getWait().until(ExpectedConditions.visibilityOfElementLocated(By.cssSelector("#dropdown[multiple]")));
```

#### elementToBeClickable
Czy webelement jest 'klikalny'/aktywny tj.: ***obecny w DOM && enabled*** np.
```java
log.info("Verify that the 'Create' button became active");
webDriverWait.until(ExpectedConditions.elementToBeClickable(buttonCreate));
```

Może zastąpić zwykłego asserta 
`assertThat(buttonCreate.isEnabled()).isTrue();`
w sytuacji, kiedy jakiś element nie jest aktywny od początku, tylko ma się stać aktywnym

Negacja - element ma być nieaktywny
```java
log.info("Verify that 'Create' button is now inactive");  
webDriverWait.until(ExpectedConditions.not(ExpectedConditions.elementToBeClickable(buttonCreate)));
```

#### visibilityOfElementLocated
Czy webelement jest: ***obecny w DOM && widoczny na stronie*** np.
```java
webDriverWait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath(WINDOW_COLOR_SELECTION_XPATH)));
```

#### invisibilityOfElementLocated
Negacja poprzedniego - czy webelement jest: ***nieobecny w DOM || niewidoczny na stronie*** np.
```java
webDriverWait.until(ExpectedConditions.invisibilityOfElementLocated(By.xpath(WINDOW_COLOR_SELECTION_XPATH)));
```
Początkowo próbowałem osiągnąć to poprzez negację not.visibilityOfElementLocated, ale to nie działało.

---
https://www.selenium.dev/selenium/docs/api/java/org/openqa/selenium/support/ui/ExpectedConditions.html