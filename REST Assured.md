#java #tools #api 

- biblioteka Java do automatyzowania testów [[REST API]]
- bazuje na [[Domain-specific language]] + Fluent Interface (możliwość stosowania [[Method Chaining]])
- działa w oparciu o [[JUnit]], albo [[TestNG]]
- wspiera wszystkie metody HTTP tj. get, post, put itd.
- wpiera syntax Gherkin (Given, When, Then)

![[Pasted image 20230125125416.png]]

## Methods

### Debugging methods

#### peek(), prettyPeek()
służą do wyprintowania całego response-header + body
```java
@Test  
public void prettyPeek() {  
    RestAssured.get(BASE_URL)  
            .prettyPeek();  
}
```

#### print(), prettyPrint()
służą do wyprintowania całego response-body
```java
@Test  
public void prettyPrint() {  
    RestAssured.get(BASE_URL)  
            .prettyPrint();  
}
```

### Convenience methods

#### getStatusCode(), getContentType()
```java
@Test  
public void convenienceMethods() {  
    Response response = RestAssured.get(BASE_URL);  
    Assert.assertEquals(response.getStatusCode(), 200);  
    Assert.assertEquals(response.getContentType(), "application/json; charset=utf-8");  
}
```

#### getHeaders()
zwraca cały response-header
```java
@Test  
public void getHeaders() {  
    Response response = RestAssured.get(BASE_URL);  
    Headers headers = response.getHeaders();  
    Assert.assertEquals(headers.getValue("server"), "GitHub.com");  
}
```

#### getHeader(String header)
zwraca value konkretnego headera
```java
@Test  
public void genericHeader() {  
    Response response = RestAssured.get(BASE_URL);  
    Assert.assertEquals(response.getHeader("server"), "GitHub.com");  
}
```

#### getTime(), getTimeIn()
zwracają response time (czas potrzebny na wysłanie reponsa z servera)
```java
@Test  
public void getResponseTime() {  
    Response response = RestAssured.get(BASE_URL);  
    System.out.println(response.getTime());  // e.g. 558
    System.out.println(response.getTimeIn(TimeUnit.MICROSECONDS));  // e.g. 558000
}
```

## [[JsonPath]] i [[GPath]]
- JsonPath i GPath to path expression languages dla JSON
- porównywalny do XmlPath dla plików XML, albo XPath dla plików HTML
- Rest Assured używa GPath notation

## Hamcrest matchers

## Rodzaje parametrów w RESTful APIs
1. Path parameters np. 
- hatetepees://zippopotam.us/**pl**/**64-530**
- hatetepees://pokeapi.co/api/v2/**pokemon**/**pikachu**/

2. Query parameters - też definiowane w URI, ale ze strukturą *?key=value* np.
- hatetepees://md5.jsontest.com/?**text**=**banana**

## Źródła:
- https://testautomationu.applitools.com/automating-your-api-tests-with-rest-assured/
- https://www.pluralsight.com/courses/rest-assured-fundamentals

