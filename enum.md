#java 

**Enum**  to typ wyliczeniowy, wyglądający podobnie jak klasa. Pozwala zadeklarować ograniczoną listę zmiennych typu *constant* ([[Coding best practices]]). 

Enum jest trochę jak [[Array]] z tym że jego elementy są z góry znane, niezmienialne, i do każdego z jego elementów można się odnieść poprzez nazwę zmiennej constant,  a nie poprzez index.

Przykład:
```java
public enum DayOfTheWeek {
	MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
}
```

## Źródła:
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/35423818?start=15#notes