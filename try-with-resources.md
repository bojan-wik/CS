#programming #java 

to konkstrukt/blok kodu wewn. którego możemy zadeklarować jakieś obiekty, użyć je, po czym zostaną one automatycznie zamknięte po wykonaniu tego bloku. Nie musimy ich sami zamykać, np.:

```java
try (PrintWriter writer = new PrintWriter(new File("test.txt"))) {
    writer.println("Hello World");
}
```

Przydatne dla takich obiektów, jak np: gniazda sieciowe, połączenia z bazami danych, referencje do plików/folderów. Niezamknięcie takich obiektów może spowodować wycieki pamięci, zwiększać niepotrzebnie zużycie CPU/pamięci etc.