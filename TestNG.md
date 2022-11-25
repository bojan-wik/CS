#tools 

TestNG, to obok [[JUnit]] najpopularniejsza biblioteka do automatyzacji testów dla Javy.

## Annotations

### Rodzaje

#### Pre-Condition(s)
- @BeforeSuite
- @BeforeTest
- @BeforeClass
- @BeforeMethod

#### Condition(s)
- @Test

#### Post-Condition(s)
- @AfterSuite
- @AfterTest
- @AfterClass
- @AfterMethod

### Kolejność wykonywania

#### Top level

![[Pasted image 20221123093922.png]]

#### @Test method level

Adnotacja @Test jest możliwa do zadeklarowania:
- per metoda
- per klasa - wtedy metody które mają być testami nie muszą mieć adnotacji @Test, ale muszą być *public* ([[Access modifiers]]) - rozwiązanie raczej żadko używane

**Standardowo** metody z adnotacją @Test wykonywane są w kolejności alfabetycznej.

Dzięki atrybutowi **priority** możemy ustalić dowolną kolejność wykonywania testów
```java
@Test (priority = 1)  
public void searchCustomer() {
	System.out.println("@Test | Search for Customer");
}  
  
@Test (priority = 2)  
public void searchProduct() {
	System.out.println("@Test | Search for Product");
}
```
Tak samo jak w [[JUnit]], tutaj też możemy zacząć od *priority = 0*.

## Źródła:
- https://github.com/bojan-wik/SeleniumWithJavaCourse/tree/master/src/Chapter18_TestNG
- https://testautomationu.applitools.com/introduction-to-testng/chapter3.html