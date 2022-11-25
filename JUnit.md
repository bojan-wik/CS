#tools

## Download and Install

#### JAR
>https://github.com/junit-team/junit4/wiki/Download-and-Install

## Adnotacje

#### @Order
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

@Order - działa już od 0, tak samo jak w [[TestNG]]

#### Assercja na to, że rzucony jest Exception
```java
@Test(expected = IllegalArgumentException.class)
    public void test9() {
        Challenge.returnTheEndOfNumber(0);
    }
```
>https://www.baeldung.com/junit-assert-exception