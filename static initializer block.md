#jave

```java
static {
	// code
}
```

Kod umieszczony w bloku `static` jest wywoływany tylko raz, na samym początku, podczas ładowania się klasy, w której został zdefiniowany.

Kod wywoływany jest przed inicjalizacją obiektu, czyli jeszcze przed samym konstruktorem.

W przypadku większej ilości bloków wywoływane są one w kolejności, w której są zadeklarowane w klasie.

Static initializer blocks są rzadko stosowane w praktyce.

## Źródła:
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/4069708#notes
- https://www.baeldung.com/java-static-instance-initializer-blocks