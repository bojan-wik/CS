#selenium 

## Metody

### getText()
Wyciąganie tekstu z webelementu, ale działa tylko z webelementami, które nie są ukryte.
Dla ukrytych webelementów muszę użyć `getAttribute("textContent")` np.
```java
assertThat(driver.findElement(By.xpath("//span[@ng-if='!isCustomCaption']")).getAttribute("textContent")).contains("0 file");
```
>https://stackoverflow.com/a/32475546

### isSelected()
Sprawdza, czy webelement jest selected, czy nie. Działa na radio button, checkbox, opcjach w menu.

Jeżeli chodzi o radio button, to działa chyba tylko na klasycznych, HTMLowych `<input type="radio">`
bo np. na Angularowym `md-radio-button` już nie działa - zwraca zawsze false.
W tym przypadku robiłem asercję po jakimś atrybucie np.
```java
assertThat(radioButtonGraphicalLogo.getAttribute("aria-checked")).isEqualTo("true");
```

### isEnabled
Sytuacja taka sama jak wyżej - nie działa dla elementów Angularowych np. `mat-radio-button`, zastąpione asercją:
```java
Assert.assertTrue(btn_DIADivision.getAttribute("class").contains("mat-radio-disabled");
```

## Code snippets

#### open link in a new tab
```java
public void openLinkInNewTab(String linkText) {  
    String clickLink = Keys.chord(Keys.CONTROL, Keys.ENTER);  
    getWait().until(ExpectedConditions.visibilityOfElementLocated(
    By.linkText(linkText))).sendKeys(clickLink);  
}
```
>https://www.tutorialspoint.com/how-to-open-a-link-in-new-tab-using-selenium-webdriver

#### switch to tab/window with expected title
[[Set]] -> Przykład użycia w testach automatycznych
#### check if element is present on the DOM
```java
    public boolean checkIfElementIsPresentOnTheDOM(By locator) {
        try {
            driver.findElement(locator);
        } catch (NoSuchElementException e) {
            return false;
        }
        return true;
    }
```
Żeby funkcja zadziałała poprawnie tj. poprawnie wyłapała wyjątek i zwróciła false w przypadku braku elementu, trzeba zaimportować
`NoSuchElementException (org.openqa.selenium)`
a nie
`NoSuchElementException (java.util)`

#### dynamic xpath
```java
String CR_SECTION_THREE_DOTS_MENU = "//div[contains(text(), '%s')]";
String sectionName = "section1";

webDriverWait.until(ExpectedConditions.elementToBeClickable
                        (By.xpath(String.format(CR_SECTION_THREE_DOTS_MENU, sectionName)))).click();
```
Ten sposób nie działa z CSS selectorami

#### iterate through list of webelements -> find element within element
```java
List<WebElement> contentTiles = driver.findElements(By.xpath("//md-card[contains(@class, 'ng-scope')]"));
for (WebElement groupTile : contentTiles) {
            System.out.println(groupTile.findElement(By.xpath(".//span[@class='group-name']")).getText());
        }
```

#### unfocus input webelement after sendKeys()
```java
JavascriptExecutor jsExec = (JavascriptExecutor) driver;
jsExec.executeScript("document.activeElement.blur()");
```
>https://forum.katalon.com/t/remove-the-focus-from-an-element-after-settext-or-sendkeys/30878/4
>https://developers.perfectomobile.com/display/TT/Unfocus+Input+Web+Element

#### upload a file
```java
@FindBy(xpath = "//input[@type='file']")  
WebElement inputBrowse;

inputBrowse.sendKeys("C:\\snap\\non-image sample file.doc");
```
- sendKeys() musi być wykonanane na webelemencie typu input (najbardziej zagnieżdżonym), nie działa na buttonie
- działa z Windowsowym dialogiem do wyszukiwania plików
- działa na Virtual Machine (Robot class nie działa na VM)
>https://sqa.stackexchange.com/questions/12851/how-can-i-work-with-file-uploads-during-a-webdriver-test

#### scroll down quasi-infinite inner-scrollbar to the last element
```java
void scrollDownInnerScrollbarToTheLastGroup() {
        log.info("Scroll down page to the last group");
        waitUntilProgressBarDisappear();
        JavascriptExecutor jsExec = (JavascriptExecutor) driver;
        String lastGroup = "";
        while (true) {
            String currentLastGroup = driver.findElement(By.xpath("(//span[@class='group-name'])[last()]")).getText();
            jsExec.executeScript("(document.getElementById('inf-wrapper')).scrollTop += 2000");
            waitUntilProgressBarDisappear();
            if (lastGroup.equals(currentLastGroup)) {
                break;
            } else {
                lastGroup = currentLastGroup;
            }
        }
    }
```
>https://csnotes.medium.com/web-scraping-infinite-scrolling-with-selenium-97f820d2e506

#### scroll down infinite scrollbar to the desired element
```java
private By paragraph = By.className("jscroll-added");

public void scrollToNthParagraph(int n) {  
    String script =  "window.scrollTo(0, document.body.scrollHeight)";  
    JavascriptExecutor jsExecutor =  (JavascriptExecutor)getDriver();  
  
    while (getNumberOfParagraphsPresent() < n) {  
        jsExecutor.executeScript(script);  
    }  
}  
  
private int getNumberOfParagraphsPresent() {  
    return getDriver().findElements(paragraph).size();  
}
```
>https://testautomationu.applitools.com/selenium-webdriver-tutorial-java/chapter10.html