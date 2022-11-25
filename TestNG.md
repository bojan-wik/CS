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

Standardowo metody z adnotacją @Test wykonywane są w kolejności alfabetycznej.

## Źródła:
- https://github.com/bojan-wik/SeleniumWithJavaCourse/tree/master/src/Chapter18_TestNG
- https://testautomationu.applitools.com/introduction-to-testng/chapter3.html