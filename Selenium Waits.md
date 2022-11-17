#selenium 

## Implicit Wait

Służy do ustawiania globalnego czasu jaki webdriver będzie czekał na dany webelement zanim rzuci “No Such Element Exception”.

Implicit Wait ustawiany jest globalnie, per cały framework testowy, na poziomie webdrivera, np.
```java
WebDriver driver = new ChromeDriver();
driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
```

## Explicit Wait

Służy do ustawiania czasu jaki webdriver będzie czekał na określony warunek ([[ExpectedConditions]]) w stosunko do danego webelementu, zanim rzuci “No Such Element Exception”.

Explicit Wait jest ustawiany poprzez utworzenie obiektu klasy WebDriverWait, np.
```java
WebDriverWait wait = new WebDriverWait(driver, 15);
```

i potem można go wywoływać w konkretnych sytuacjach, np.
```java
wait.until(ExpectedConditions.elementToBeClickable(startButton)).click();
```

## Fluent Wait

Podobny do Explicit Wait, ale bardziej customizowalny. Tutaj poza czasem oczekiwania możemy dodatkowo ustawić polling time (co ile czasu ma sprawdzać DOM), albo jakie [[Exceptions]] ma ignorować, np.
```java
Wait<WebDriver> wait = new FluentWait<>(driver).  
        withTimeout(Duration.ofSeconds(5)).  
        pollingEvery(Duration.ofSeconds(1)).
        ignoring(NoSuchElementException.class);
```

i potem można go wywoływać w konkretnych sytuacjach, jak w przypadku Explicit Wait
```java
wait.until(ExpectedConditions.elementToBeClickable(startButton)).click();
```

---
- https://testautomationu.applitools.com/selenium-webdriver-tutorial-java/chapter9.html