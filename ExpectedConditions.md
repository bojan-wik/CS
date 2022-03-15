# ExpectedConditions
#selenium 

##### attributeContains
Czy webelement->***atrybut zawiera konkretny string*** np.
```java
webDriverWait.until(ExpectedConditions.attributeContains(By.xpath(SECTION_TAG_PREVIEW_CONTENT_XPATH), "style", "rgb(109, 139, 184)"));
```

##### elementToBeClickable
Czy webelement jest 'klikalny'/aktywny tj.: ***obecny w DOM + enabled*** np.
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

##### visibilityOfElementLocated
Czy webelement jest: ***obecny w DOM + widoczny na stronie*** np.
```java
webDriverWait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath(WINDOW_COLOR_SELECTION_XPATH)));
```

---
https://www.selenium.dev/selenium/docs/api/java/org/openqa/selenium/support/ui/ExpectedConditions.html