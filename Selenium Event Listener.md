#selenium 

Przydatne w tworzeniu logów z odpalanych testów.

## EventFiringWebDriver
to klasa wrapper dla webdrivera, np.:

```java
public class BaseTest {  
  
    private EventFiringWebDriver driver;  
 
    @BeforeClass  
    public void setUp() {  
        driver = new EventFiringWebDriver(new ChromeDriver());  
        driver.register(new EventListener());  
    }
}    
```

## WebDriverEventListner
to interfejs do zaimplementowania, aby móc nasłuchiwać i wyłapywać eventy/akcje webdrivera, np:

```java
public class EventListener implements WebDriverEventListener {  
  
    @Override  
    public void beforeAlertAccept(WebDriver webDriver) {  
        System.out.println("Accepting an alert");  
    }  
  
    @Override  
    public void beforeAlertDismiss(WebDriver webDriver) {  
        System.out.println("Dismissing an alert");  
    }  
  
    @Override  
    public void beforeNavigateTo(String s, WebDriver webDriver) {  
        System.out.println("Navigating to: " + s);  
    }  
  
    @Override  
    public void beforeNavigateBack(WebDriver webDriver) {  
        System.out.println("Navigating back one page");  
    }  
   
    @Override  
    public void beforeNavigateForward(WebDriver webDriver) {  
        System.out.println("Navigating forward one page");  
    }  
     
    @Override  
    public void beforeNavigateRefresh(WebDriver webDriver) {  
        System.out.println("Refreshing the page");  
    }  
 
    @Override  
    public void beforeClickOn(WebElement webElement, WebDriver webDriver) {  
        System.out.println("Clicking on: " + webElement.getText());  
    }  

    @Override  
    public void beforeScript(String s, WebDriver webDriver) {  
        System.out.println("Running script: " + s);  
    }
}
```

## Źródła:
- https://testautomationu.applitools.com/selenium-webdriver-tutorial-java/chapter13.html