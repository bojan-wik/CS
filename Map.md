#java 

- interfejs wchodzący w skład frameworka [[Collections]]
- Map nie implementuje frameworka [[Collections]], w odróżnieniu od [[List]] i [[Set]] 
- przechowuje elementy w postaci par klucz-wartość (key-value)
- do danego klucza może być przypisana tylko jedna wartość
- klucze są unikalne, nie mogą być zduplikowane tzn. jeśli użyjemy danego klucza ponownie, to jego wartość zostanie nadpisana
- Map jest nieupożądkowany - elementy zwracane są w randomowej kolejności
- Map to to samo co Dictionary w Pythonie

```java
Map<String, String> englishSpanishDict = new HashMap<>();
```

Dodawanie elementów (para key-value)
```java
englishSpanishDict.put("house", "casa");
englishSpanishDict.put("homie", "tio");
```

Usuwanie elementów
```java
englishSpanishDict.remove("house");
// albo
englishSpanishDict.remove("house", "casa");
```

Zastąpienie jednej wartości inną wartością
```java
englishSpanishDict.replace("homie", "ese");
// albo
englishSpanishDict.replace("homie", "tio", "ese");
```

Sprawdzanie, czy dany klucz już istnieje
```java
englishSpanishDict.containsKey("homie");
```

Wyprintowanie elementów
```java
for (String key : englishSpanishDict.keySet()) {  
    System.out.println(key + ": " + englishSpanishDict.get(key));  
}
```

