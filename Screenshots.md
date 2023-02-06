#selenium #playwright 

- Generalnie robienie screenshotów ma sens tylko dla testów, które failują.
- Trzeba pamiętać żeby folder ze screenshotami wyekskludować z Gita - dodać go do pliku [[gitignore]]
- Poniższe metody opierają się na adnotacjach z [[TestNG]]. Napisanie tego samego w [[JUnit]] jest bardziej skomplikowane

## Selenium

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

## Playwright

```java
@AfterMethod  
void takeScreenshotIfTestFailsAndCloseBrowserContext(ITestResult result) {  
    if (!result.isSuccess()) {  
        page.screenshot(new Page.ScreenshotOptions().setPath(Paths.get("screenshots/"  
                + result.getName() + ".png")));  
    }  
  
    browserContext.close();  
}
```

## Źródła: 
- https://testautomationu.applitools.com/selenium-webdriver-tutorial-java/chapter12.html
- https://github.com/bojan-wik/SeleniumTAU/blob/master/src/test/java/base/BaseTest.java