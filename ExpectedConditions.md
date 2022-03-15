# ExpectedConditions
#selenium 

##### elementToBeClickable
Przydatny w sytuacjach, w których jakiś element ma być 'klikalny'/aktywny tj. widoczny w DOMie + enabled
```java
log.info("Verify that the 'Create' button became active");
webDriverWait.until(ExpectedConditions.elementToBeClickable(buttonCreate));
```
Może zastąpić zwykłego asserta 
`assertThat(buttonCreate.isEnabled()).isTrue();`
w sytuacji, kiedy jakiś element nie jest aktywny od początku, tylko ma się stać aktywnym