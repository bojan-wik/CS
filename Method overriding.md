#programming #java 

Ficzer, który pozwala na utworzenie w sub-klasie metody, która już istnieje w super-klasie (ma tą samą nazwę i listę parametrów)

Mimo, że overriding zachodzi automatycznie, zaleca się stosowanie adnotacji `@Override`
- poprawia to czytelność kodu
- wywala błąd, kiedy myślimy, że nadpisujemy jakąś metodę, a tak faktycznie nie jest np. na wskutek literówki

Można nadpisywać tylko metody `instace` ([[static vs instance]])
Nie można nadpisać metod, które są: 
- `static`
- `final` 
- `private`

## Źródła:
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/10261274#overview