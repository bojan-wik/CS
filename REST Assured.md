#java #tools #api 

- biblioteka Java do automatyzowania testów [[REST API]]
- bazuje na [[Domain-specific language]] + Fluent Interface (możliwość stosowania [[Method Chaining]])
- działa w oparciu o [[JUnit]], albo [[TestNG]]
- wspiera wszystkie metody HTTP tj. get, post, put itd.
- wpiera syntax Gherkin (Given, When, Then)

![[Pasted image 20230125125416.png]]

## JsonPath i GPath
- JsonPath i GPath to path expression languages dla JSON
- porównywalny do XmlPath dla plików XML, albo XPath dla plików HTML
- Rest Assured używa GPath notation

## Validating response-header

### with Simple Response

#### Debugging methods

##### peek(), prettyPeek()
służą do wyprintowania całego response-header + body
```java
@Test  
public void prettyPeek() {  
    RestAssured.get(BASE_URL)  
            .prettyPeek();  
}
```

##### print(), prettyPrint()
służą do wyprintowania całego response-body
```java
@Test  
public void prettyPrint() {  
    RestAssured.get(BASE_URL)  
            .prettyPrint();  
}
```

#### Convenience methods

##### getStatusCode(), getContentType()
```java
@Test  
public void convenienceMethods() {  
    Response response = RestAssured.get(BASE_URL);  
    Assert.assertEquals(response.getStatusCode(), 200);  
    Assert.assertEquals(response.getContentType(), "application/json; charset=utf-8");  
}
```

##### getHeaders()
zwraca cały response-header
```java
@Test  
public void getHeaders() {  
    Response response = RestAssured.get(BASE_URL);  
    Headers headers = response.getHeaders();  
    Assert.assertEquals(headers.getValue("server"), "GitHub.com");  
}
```

##### getHeader(String header)
zwraca value konkretnego headera
```java
@Test  
public void genericHeader() {  
    Response response = RestAssured.get(BASE_URL);  
    Assert.assertEquals(response.getHeader("server"), "GitHub.com");  
}
```

##### getTime(), getTimeIn()
zwracają response time (czas potrzebny na wysłanie reponsa z servera)
```java
@Test  
public void getResponseTime() {  
    Response response = RestAssured.get(BASE_URL);  
    System.out.println(response.getTime());  // e.g. 558
    System.out.println(response.getTimeIn(TimeUnit.MICROSECONDS));  // e.g. 558000
}
```




### with ValidatableResponse

#### header()
```java
@Test  
public void headerTest() {  
    RestAssured.get(BASE_URL)  
            .then().assertThat()  
            .header("x-ratelimit-limit", stringValue -> Integer.parseInt(stringValue), Matchers.equalTo(60));  
}
```

#### headers()
```java
@Test  
public void headersTest() {  
    RestAssured.get(BASE_URL)  
            .then().assertThat()  
            .headers("content-encoding", "gzip",  
                    "access-control-allow-origin", "*");  
}
```

To samo z wykorzystaniem zewn. kolekcji Map
```java
Map<String, String> expectedHeaders = Map.of(  
        "content-encoding", "gzip",  
        "access-control-allow-origin", "*");

@Test  
public void headersTest() {  
    RestAssured.get(BASE_URL)  
            .then().assertThat()  
            .headers(expectedHeaders);  
}
```



## Validating response-body (aka payload)

### with Simple Response

##### JsonPath.get()
służy do traversowania po jsonie
```java
@Test  
public void jsonPathReturnMap() {  
    Response response = RestAssured.get("https://api.github.com/rate_limit");  
    JsonPath jsonPath = response.body().jsonPath();  
  
    Map<String, Object> fullResponseJson = jsonPath.get();  
    System.out.println(fullResponseJson.toString());  
  
    int resourcesCoreLimit_value = jsonPath.get("resources.core.limit");  
    Assert.assertEquals(resourcesCoreLimit_value, 60);  
  
    int resourcesGraphqlLimit_value = jsonPath.get("resources.graphql.limit");  
    Assert.assertEquals(resourcesGraphqlLimit_value, 0);  
}
```

### with ValidatableResponse

##### body()
```java
@Test  
    public void complexBodyExample() {  
        RestAssured.get(BASE_URL + "https://api.github.com/users/bojan-wik")  
                .then()  
//                .body("url", containsString("bojan-wik"))  
                .body("url", response -> containsString(response.body().jsonPath().get("login")));  
    }
```

##### rootPath()
```java
@Test  
public void nestedBodyValidation() {  
    RestAssured.get("https://api.github.com/rate_limit")  
            .then()  
            .rootPath("resources.core")  
                .body("limit", equalTo(60))  
                .body("resource", equalTo("core"))  
            .rootPath("resources.search")  
                .body("remaining", lessThanOrEqualTo(10))  
                .body("resource", notNullValue());  
}
```

## Hamcrest matchers
dają nam więcej możliwości i elastyczności w robieniu asercji.

Przykład z wykorzystaniem podst. *ValidatableResponse*:
```java
@Test  
public void basicValidatableExample() {  
    RestAssured.get(BASE_URL)  
            .then().assertThat()  
                .statusCode(200)  
                .contentType(ContentType.JSON)  
                .header("x-ratelimit-limit", "60");  
}
```

Przykład z wykorzystaniem *Hamcrest matchers*:
```java
@Test  
public void simpleHamcrestMatchers() {  
    RestAssured.get(BASE_URL)  
            .then().assertThat()  
                .statusCode(Matchers.lessThan(300))  
                .header("cache-control", Matchers.containsStringIgnoringCase("public"))  
                .time(Matchers.lessThanOrEqualTo(1L), TimeUnit.SECONDS)  
                .header("etag", Matchers.notNullValue());  
}
```

## Rodzaje parametrów w RESTful APIs
1. Path parameters np. 
- hatetepees://zippopotam.us/**pl**/**64-530**
- hatetepees://pokeapi.co/api/v2/**pokemon**/**pikachu**/

2. Query parameters - też definiowane w URI, ale ze strukturą *?key=value* np.
- hatetepees://md5.jsontest.com/?**text**=**banana**

## Mapowanie response-body/paylod do Java-obiektów

**Marshalling** to proces konwertowania java-obiekt -> XML/JSON.
**Unmarshalling** działa w drugą stronę: konwersja XML/JSON -> java-obiekt.

To w zasadzie synonimy serializacji/deserializacji danych o których już wcześniej się uczyłem w kursie na TAU.

### Przykład
```java
@JsonIgnoreProperties(ignoreUnknown = true)  
public class User {  
  
    private String login;  
    private int id;  
  
    @JsonProperty("public_repos")  
    private int publicRepos;  
  
    public String getLogin() {  
        return login;  
    }  
  
    public int getId() {  
        return id;  
    }  
  
    public int getPublicRepos() {  
        return publicRepos;  
    }  
}
```

```java
public class ObjectMapping {  
  
    public static final String BASE_URL = "https://api.github.com/users/bojan-wik";  
  
    @Test  
    public void objectMappingTest1() {  
        User user = RestAssured.get(BASE_URL)  
                .as(User.class);  
  
        Assert.assertEquals(user.getLogin(), "bojan-wik");  
        Assert.assertEquals(user.getId(), 23448817);  
        Assert.assertEquals(user.getPublicRepos(), 17);  
    }
}
```


## Metody HEAD, OPTIONS, POST, PATCH, DELETE

##### HEAD, OPTIONS

```java
public static final String BASE_URL = "https://api.github.com/";  
  
@Test  
public void headTest() {  
    RestAssured.head(BASE_URL)  
            .then().assertThat()  
                .statusCode(200)  
                .body(Matchers.emptyOrNullString())  
                .header("Accept-Ranges", "bytes");  
}  
  
@Test  
public void optionsTest() {  
    RestAssured.options(BASE_URL)  
            .then().assertThat()  
            .statusCode(204)  
            .header("access-control-allow-methods", Matchers.equalTo("GET, POST, PATCH, PUT, DELETE"))  
            .body(Matchers.emptyOrNullString());  
}
```

##### POST, PATCH, DELETE

```java

public static final String BASE_URL = "https://api.github.com/user/repos";  
public static final String TOKEN = "123456789";  
  
@Test  
public void postTest() {  
    RestAssured  
            .given()  
                .header("Authorization", "token " + TOKEN)  
                .body("{\"name\": \"deleteme\"}")  
            .when()  
                .post(BASE_URL)  
            .then()  
                .statusCode(201);  
}  
  
@Test  
public void patchTest() {  
    RestAssured  
            .given()  
                .header("Authorization", "token " + TOKEN)  
                .body("{\"name\": \"deleteme-patched\"}")  
            .when()  
                .patch("https://api.github.com/repos/bojan-wik/deleteme")  
            .then()  
                .statusCode(200);  
}  
  
@Test  
public void deleteTest() {  
    RestAssured  
            .given()  
                .header("Authorization", "token " + TOKEN)  
            .when()  
                .delete("https://api.github.com/repos/bojan-wik/deleteme-patched")  
            .then()  
                .statusCode(204);  
}
```


## Code snippets:

#### dokonaj autentykacji sesji

Dzięki takiej autentykacji nie trzeba potem wykonywać każdorazowo stepów logowania przed każdym testem (przykład z entieres).
```java
-> NtrsLoginAuthentication.java
```
>https://stackoverflow.com/questions/51214120/rest-assured-basic-auth-issue

### RESPONSE-body

#### sprawdź czy value jednego node zawiera w sobie value innego node
```java
@Test
public void complexBodyExample() {
    RestAssured.get("https://api.github.com/users/bojan-wik")
            .then()
//            .body("url", containsString("bojan-wik"))
            .body("url", response -> containsString(response.body().jsonPath().get("login")));
}
```
>https://app.pluralsight.com/course-player?clipId=7f2cf58b-3347-4fd8-80e2-2a3c680adb0f

#### sprawdź jaki jest size JSON arraya z response
```java
public Integer getRestJsonArraySize(String apiBodyService) {
        Response response = given().spec(specification)
                .headers(headers)
                .cookies(cookies)
                .when()
                .get(apiBodyService);
        JsonPath jsonPath = new JsonPath(response.asString());
        return jsonPath.getInt("data.size()");
    }
```
> https://www.tutorialspoint.com/explain-how-to-get-the-size-of-a-json-array-response-in-rest-assured

**Przykład (z entieres):** 
- wysyłam request GET na endpoincie, który ma mi zwrócić wszystkich userów w systemie. 
- Chcę sprawdzić, czy jest dodany chociaż jeden
- robię w tym przypadku asercję, że status code = 200 i getRestJsonArraySize() > 0


### RESPONSE-header

#### sprawdź, czy data z response-header odpowiada aktualnej dacie
```java
@Test  
public void test() {  
    RestAssured.get(BASE_URL).then().assertThat()  
            .header("date", 
            date -> LocalDate.parse(date, DateTimeFormatter.RFC_1123_DATE_TIME),  
                    OrderingComparison.comparesEqualTo(LocalDate.now()));  
}
```
>https://app.pluralsight.com/course-player?clipId=dd7abb6d-9554-447b-8d2f-c48319825ef6

#### porównaj ze sobą valuesy dwóch różnych response-header
```java
@Test  
public void test() {  
    RestAssured.get("https://api.github.com/").then().assertThat()  
            .header("x-ratelimit-limit", 
            response -> greaterThan(response.header("x-ratelimit-remaining")));  
}
```

## Źródła:
- https://testautomationu.applitools.com/automating-your-api-tests-with-rest-assured/
- https://www.pluralsight.com/courses/rest-assured-fundamentals

