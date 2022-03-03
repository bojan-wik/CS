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