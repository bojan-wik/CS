#java #tools #api 

- biblioteka Java do automatyzowania testów [[REST API]]
- bazuje na [[Domain-specific language]] + Fluent Interface (możliwość stosowania [[Method Chaining]])
- działa w oparciu o [[JUnit]], albo [[TestNG]]
- wspiera wszystkie metody HTTP tj. get, post, put itd.
- wpiera syntax Gherkin (Given, When, Then)

![[Pasted image 20230125125416.png]]

## Methods

### Debugging methods

#### peek() i prettyPeek()
służą do wyprintowania response header + body, np.:
```java
@Test  
public void prettyPeek() {  
    RestAssured.get(BASE_URL)  
            .prettyPeek();  
}
```

#### print() i prettyPrint()
służą do wyprintowania response body, np.L
```java
@Test  
public void prettyPrint() {  
    RestAssured.get(BASE_URL)  
            .prettyPrint();  
}
```

### Convenience methods

#### [[JsonPath]] i [[GPath]]
- JsonPath i GPath to path expression languages dla JSON
- porównywalny do XmlPath dla plików XML, albo XPath dla plików HTML
- Rest Assured używa GPath notation

#### Hamcrest matchers

#### Rodzaje parametrów w RESTful APIs
1. Path parameters np. 
- hatetepees://zippopotam.us/**pl**/**64-530**
- hatetepees://pokeapi.co/api/v2/**pokemon**/**pikachu**/

2. Query parameters - też definiowane w URI, ale ze strukturą *?key=value* np.
- hatetepees://md5.jsontest.com/?**text**=**banana**

## Źródła:
- https://testautomationu.applitools.com/automating-your-api-tests-with-rest-assured/
- https://www.pluralsight.com/courses/rest-assured-fundamentals

