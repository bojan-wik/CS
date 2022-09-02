# Code snippets
#java #selenium 

#### extracting last two digits and last digit of the number
```java
int number = 111;
int lastTwoDigits = number % 100;  
int lastDigit = lastTwoDigits % 10;
```

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

#### extract digit from a string and convert it to int
```java
String str = "The price of the book is $49";
String numberOnly = str.replaceAll("[^0-9]", "");
int numberOnlyInt = Integer.parseInt(numberOnly);
```

#### dynamic xpath
```java
String CR_SECTION_THREE_DOTS_MENU = "//div[contains(text(), '%s')]";
String sectionName = "section1";

webDriverWait.until(ExpectedConditions.elementToBeClickable
                        (By.xpath(String.format(CR_SECTION_THREE_DOTS_MENU, sectionName)))).click();
```

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

#### scroll down infinite inner scrollbar
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