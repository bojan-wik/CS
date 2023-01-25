#programming #java 

**try-with-resources** to konkstrukt/blok kodu wewn. którego możemy zadeklarować jakieś obiekty, użyć je, po czym zostaną one automatycznie zamknięte po wykonaniu tego bloku. Nie musimy ich sami zamykać.

>Na to pojęcie trafiłem przy okazji nauki frameworka [[Playwright]], gdzie w bloku *try-with-resources* deklarowało się i inicjalizowało obiekty klasy Playwright służące do inicjalizowania przeglądarki i otwierania konkretnej strony www.

Blok *try-with-resources* może zastąpić nam w niektórych przypadkach blok *try-catch-finally* ([[Exceptions]]).

## Przykład: 
Niektóre obiekty wymagają zamknięcia. Takie obiekty to m.in. gniazda sieciowe, połączenia z bazami danych, referencje do plików/folderów. Niezamknięcie takich obiektów może spowodować wycieki pamięci, zwiększać niepotrzebnie zużycie CPU/pamięci etc.

1. W bloku *try-catch-finally* musimy zamknąć takie obiekty sami, np.:
```java
public static void main(String[] args) throws IOException {  
        FileWriter file = null;  
        
        try {  
            file = new FileWriter("test-try-catch-finally.txt");  
            file.write("test try-catch-finally");  
        } finally {  
            if (file != null) {  
                file.close();  
            }  
        }
    }
```

2. W bloku *try-with-resources* takiego zamknięcia nie musimy robić, odbywa się to automatycznie, np.:
```java
public static void main(String[] args) throws IOException {  
        try (FileWriter file = new FileWriter("test-try-with-resources.txt")) {  
            file.write("test try-with-resources");  
        }  
    }
```

## Inne przykłady:
- https://github.com/bojan-wik/UdemyJavaMasterclass/blob/master/src/section14/inputOutput/Locations.java

## Źródła:
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/4901460#notes