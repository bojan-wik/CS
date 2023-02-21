#java 

**Enum**  to typ wyliczeniowy, wyglądający podobnie jak klasa. Pozwala zadeklarować ograniczoną listę zmiennych typu *constant* ([[Coding best practices]]). 

Enum jest trochę jak [[Array]] z tym że jego elementy są z góry znane, niezmienialne, i do każdego z jego elementów można się odnieść poprzez nazwę zmiennej constant,  a nie poprzez index.

**Przykład:**
```java
public enum DayOfTheWeek {
	MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
}
```

## Zastosowanie w automatyzacji testów

Z enumami w automatyzacji testów spotkałem się pierwszy raz w projekcie benchowym z Playwrigtha, gdzie stosował je w swoim kodzie Marcin. Do tej pory w żadnych innych frameworkach testowych (Pubcenter, Medcin) nie widziałem wykorzystania enumów.

### Przykład:
W formularzu dodawania użytkownika jest dropdown z polem do wyboru kraju.

#### moja standardowa metoda

```java
/** Sets the country randomly from the available options in the dropdown. */
public AddCandidatePage setCountry() {
    Locator countryDropdownOption = page.locator("locator");
    randomIndex = generateRandomNumberWithinRange(1, countryDropdownOption.count() - 1);
    countryDropdown.selectOption(new SelectOption().setIndex(randomIndex));
    return this;
}
```

#### podejście z wykorzystaniem enum

```java
public enum Country {
    GERMANY("Germany"),
    ITALY("Italy"),
    POLAND("Poland"),
    ROMANIA("Romania"),
    UNITED_KINGDOM("United Kingdom");

    /* Generate random String from Country enum */
    public static Country generateRandomCountry() {
        Country[] values = Country.values();
        int length = values.length;
        int randIndex = new Random().nextInt(length);
        return values[randIndex];
    }
}
```

W tym projekcie benczowym Marcin zastosował także [[DTO Pattern in Java]]. W kontekście tego wzorca bardziej sensowne mogło być zastosowanie także enumów zamiast zwykłej metody, którą ja napisałem.

## Źródła:
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/35423818?start=15#notes