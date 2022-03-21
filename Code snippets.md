# Code snippets
#java #selenium 

##### scroll down infinite inner scrollbar
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

##### upload a file
```java
@FindBy(xpath = "//input[@type='file']")  
WebElement inputBrowse;

inputBrowse.sendKeys("C:\\snap\\non-image sample file.doc");
```
- sendKeys() musi być wykonanane na webelemencie typu input (najbardziej zagnieżdżonym), nie działa na buttonie
- działa z Windowsowym dialogiem do wyszukiwania plików
- działa na Virtual Machine (Robot class nie działa na VM)
>https://sqa.stackexchange.com/questions/12851/how-can-i-work-with-file-uploads-during-a-webdriver-test