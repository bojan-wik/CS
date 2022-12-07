#tools 

TestNG, to obok [[JUnit]] najpopularniejsza biblioteka do automatyzacji testów dla Javy.

## I. Annotations

### 1. Rodzaje

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

### 2. Kolejność wykonywania

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

## III. Assertions
- Hard assert - w momencie jak jakaś assercja failuje to skrypt nie idzie dalej i przeskakuje do następnego testu
- Soft assert - nawet jak jakaś asserscja failuje to skrypt jest dalej wykonywany

## Źródła:
- https://github.com/bojan-wik/SeleniumWithJavaCourse/tree/master/src/Chapter18_TestNG
- https://testautomationu.applitools.com/introduction-to-testng/chapter3.html