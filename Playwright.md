#playwright

- defaultowo odpala testy w trybie headless


##### Problem ze zbyt długim wykonywaniem metody close() na obiektach klas Playwright i/albo Browser
```java
@AfterClass  
public static void closeBrowser() {  
    browser.close();
    playwright.close();  
}
```

Przyczyna problemu leżała w ustawieniu `setChannel("chrome")`
```java
@BeforeClass  
public static void launchBrowser() {  
    playwright = Playwright.create();  
    browser = playwright.chromium().launch(new BrowserType.LaunchOptions()     
            .setChannel("chrome")
    );  
}
```

Na komputerach firmowych Chrome może być odpalany z jakimis dodatkowymi skryptami. Playwright ma z tym problemy i stąd to opóżnienie.
>https://github.com/microsoft/playwright/issues/18881#issuecomment-1322309414

## Źródła:
- https://app.pluralsight.com/course-player?clipId=352fdbda-22b3-4a53-99af-dfd791c083de