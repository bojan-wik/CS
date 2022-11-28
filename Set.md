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
* Switching to currently opened window or tab 
* @param windowTitle Expected window or tab title
*/
public void switchToWindow(String windowTitle) {  
    Set<String> windowHandles = driver.getWindowHandles();  
    System.out.println("Number of opened windows/tabs: " + windowHandles.size());  
  
    System.out.println("Window handles: ");  
    windowHandles.forEach(windowHandle -> System.out.println(windowHandle));  
  
    for (String windowHandle : windowHandles) {  
        System.out.println("Switching to window: " + windowHandle);  
        driver.switchTo().window(windowHandle);  
  
        String currentWindowTitle = driver.getTitle();  
        System.out.println("Current window title: " + currentWindowTitle);  
        if (currentWindowTitle.equals(windowTitle)) {  
            break;  
        }  
    }  
}
```