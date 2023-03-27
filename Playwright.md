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


## Code snippets

#### select date in calendar/date-picker
```java
-> EditCandidatePage_DatePicker.java
```
> https://angiejones.tech/how-to-select-dates-from-date-pickers/

Przykład jest w Selenium, ale jak miałem zautomatyzować kalendarz *Entieresa* to bardzo łatwo można było to przełożyć na kod w Playwright.

Samą klasę DatePicker (odpowiedzialną za obsługę kalendarza) zamodelowałem jako [[Inner Class]] ponieważ komponent kalendarza był częścią tylko i wyłącznie EditCandidatePage - nie dało się do niego dostać z żadnego innego miejsca w aplikacji. Wtedy moim zdaniem ma to sens.

**Parsing a name-of-month string to get a `Month` enum object**
Dodatkowo napotkałem na problem z przekonwertowaniem polskiej nazwy miesiąca na angielską. Nie ma takiej funkcji wbudowanej, więc posiliłem się kodem z tego wątku (Name → `Month` object):
>https://stackoverflow.com/a/39220766

## Źródła:
- https://app.pluralsight.com/course-player?clipId=352fdbda-22b3-4a53-99af-dfd791c083de