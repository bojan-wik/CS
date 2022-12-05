#selenium 

Generalnie robienie screenshotów ma sens tylko dla testów, które failują.

```java
@AfterMethod  
public void takeScreenshotIfTestFails(ITestResult result) {  
    if (!result.isSuccess()) {  
        TakesScreenshot camera = (TakesScreenshot)driver;  
        File screenshot = camera.getScreenshotAs(OutputType.FILE);  
        try {  
            Files.move(screenshot, new File("screenshots/" + result.getName() + ".png"));  
        } catch (IOException ioException) {  
            ioException.printStackTrace();  
        }  
    }  
}
```

Trzeba pamiętać żeby folder ze screenshotami wyekskludować z Gita - dodać go do pliku [[gitignore]]

## Źródła: 
- https://testautomationu.applitools.com/selenium-webdriver-tutorial-java/chapter12.html
- https://github.com/bojan-wik/SeleniumTAU/blob/master/src/test/java/base/BaseTest.java