#java 

```java
Set<String> fruits = new HashSet<>();
```

Dodawanie elementów
```java
fruits.add("apple");  
fruits.add("banana");  
fruits.add("lemon");  
fruits.add("orange");
```

Usuwanie elementów
```java
fruits.remove("lemon");
```

Sprawdzenie, czy dany element istnieje
```java
System.out.println(fruits.contains("kiwi"));
```

Sprawdzenie rozmiaru kolekcji
```java
System.out.println(fruits.size());
```

Loopowanie po elementach
```java
// looping - iterator  
  
Iterator<String> i = fruits.iterator();  
while (i.hasNext()) {  
    System.out.println(i.next());  
}  
  
// looping - for each loop  
  
for (String fruit : fruits) {  
    System.out.println(fruit);  
}  
  
// looping - forEach()
  
fruits.forEach(fruit -> System.out.println(fruit));
```

## Przykład użycia w testach automatycznych

W przypadku kiedy mamy otwartych więcej niż jedno okno/tab przeglądarki i chcemy się po nich poruszać.

```java
/**  
 * Switching to currently opened window or tab * @param by "title" or "url"  
 * @param titleOrUrl Expected window/tab title or URL (complete or URL path)  
 */
 public void switchToWindow(String by, String titleOrUrl) {  
    Set<String> windowHandles = driver.getWindowHandles();  
    System.out.println("Number of opened windows/tabs: " + windowHandles.size());  
  
    for (String windowHandle : windowHandles) {  
        driver.switchTo().window(windowHandle);  
        switch (by) {  
            case "title":  
                String currentWindowTitle = driver.getTitle();  
                if (currentWindowTitle.equals(titleOrUrl)) {  
                    System.out.println("Switching to window with title: " + currentWindowTitle);  
                    break;                
                 }  
                break;  
            case "url":  
                String currentWindowURL = driver.getCurrentUrl();  
                if (currentWindowURL.contains(titleOrUrl)) {  
                    System.out.println("Switching to window with URL: " + currentWindowURL);  
                    break;                
                 }  
                break;  
            default:  
                throw new IllegalArgumentException("No such option in the switch statement");  
        }  
    }  
}
```
> https://testautomationu.applitools.com/selenium-webdriver-tutorial-java/chapter11.html
