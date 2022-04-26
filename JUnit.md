# JUnit
#tools

## Adnotacje

Żeby @Order działał poprawnie muszę dodatkowo przed klasą testową dodać adnotację @TestMethodOrder np.
```java
@TestMethodOrder(MethodOrderer.OrderAnnotation.class)
public class FooServiceIT {

    @Test
    @Order(1)
    public void testUploadSuccess() {
        System.out.println("1");
    }

    @Test
    @Order(2)
    public void testDownloadSuccess() {
        System.out.println("2");
    }

    @Test
    @Order(3)
    public void testDeleteSuccess() {
        System.out.println("3");
    }
}
```
Chyba tyczy się to sytuacji z JUnit 5 i nowszym
>https://stackoverflow.com/questions/54947645/junits-testmethodorder-annotation-not-working

@Order - działa już od 0, tak samo jak w TestNG