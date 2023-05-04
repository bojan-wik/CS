#programming #java 

## I. Nazewnictwo

**Sposoby zapisu:**
* snake_case
* camelCase
* PascalCase
* kebab-case

Tylko jeden sposób powinien być używany w całym projekcie. Nie powinno się ich mieszać

### Package
- nazwa zaczynająca się od małej litery,
- nazwa unikalna
- z reguły składająca się URLa napisanego od końca np.
```
com.roche
com.timbuchalka.autoboxing
```

### Class
- nazwa zaczynająca się od dużej litery
- pisana camelCase
- konkretnie opisująca co się w niej zawiera (*specific*)
- będąca rzeczownikiem np.
```
Account, Storage, RequestBody, Response
```

**Tips:** zamiast ogólnej nazwy klasy \*Manager.java można użyć czegoś bardziej konkretnego np.
`Builder, Writer, Reader, Handler, Container`

### Interface
- nazwa zaczynająca się od dużej litery,
- pisana camelCase

### Variable
- nazwa zaczynająca się od małej litery
- konkretna, najlepiej składająca się z max. dwóch słów
- pisana camelCase np.
```
i, minNumber, arrayOfNames
```

#### Constant 
(zmienne typu `static final`)
- nazwa powinna być pisana dużymi literami 
- i z użyciem snake_case np.
```
CONNECTION_LIMIT, POOL_SIZE, BATCH_SIZE
```

#### Boolean
* nazwa powinna formułować pytanie
* zaczynać się od "is" np.
```
isValidUser, isOpen, isClosed
```

### Method
* nazwa zaczynająca się od małej litery,
* pisana camelCase,
* z reguły zaczynająca się od czasownika, opisująca co robi dana metoda np.
```
getData(), sendData(), fetchUser()
```

**Naming anti-patterns:**
- dana metoda robi więcej niż wskazuje jej nazwa
- nazwy zawierające 'and', 'or', 'if' - wtedy dana metoda powinna zostać rozbita na mniejsze metody np.
![[Pasted image 20230324150449.png]]

## II. Implementowanie metod

### Return type
czego nie zwracać:
- wartości null - zamiast tego np. `Collections.emptyList()`
- tzw. magic numbers, czyli wartości, których znaczenie niekoniecznie będzie znane dla innych np. -1, 0, 1 - zamiast tego np. rzuć konkretnym wyjątkiem

### Parametry
1. Liczba parametrów - generalna zasada mówi, że:
	- 0-2 parametry - OK
	- 3 - unikać
	- 4 i więcej - refaktorować i zbijać liczbę parametrów np. poprzez podzielenie metody, obudowanie parametrów w jakiś obiekt etc.
2. Unikać tzw. flag arguments, czyli booleanów jako argumentów
3. Unikać tzw. magic numbers - przypisywać je do zmiennych i dopiero te zmienne przekazywać jako parametry
4. Zasada 'Fail Fast', czyli wyłapywać błędy z niepoprawnych przekazywanych argumentów najszybciej jak się da ([[Exceptions]] -> Podejście LBYL)

## Zasada DRY
Don't Repeat Yourself

## Źródła:
* https://medium.com/@Bigscal-Technologies/a-guide-to-achieve-clean-code-and-best-coding-practices-6b3f0eaa7fa4
* https://app.pluralsight.com/library/courses/java-writing-readable-maintainable-code/table-of-contents
* https://martinfowler.com/bliki/FlagArgument.html