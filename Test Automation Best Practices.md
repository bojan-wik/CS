#selenium #playwright 

![[Pasted image 20220923110742.png]]
Test Automation pyramid

## I. Zasada FIRST

Testy powinny być:
- **F**ast
- **I**solated/independent
- **R**epeteable
- **S**elf-validating
- **T**imely (aktualne)

### Isolated/independent 
czyli testy niezależne od siebie nawzajem
![[Pasted image 20230317145344.png]]

## Self-validating
i jednocześnie self-contained
![[Pasted image 20230321145427.png]]

## II. Zasada BICEP

1. **Boundary conditions** (standardowe wartości brzegowe, edge casy)

2. **Inverse Relationships**, czyli testowanie jednocześnie:
	- konkretnego test case np. czy mail zawierający słowo 'reklama' trafił do folderu Spam
	- i jego odwrotności np. czy mail nie zawierający słowa 'reklama' trafił do folderu Inbox a nie do Spamu

3. **Cross-checking**, czyli np. mam test, gdzie w sklepie internetowym dodaję do koszyka i kupuję jakiś produkt. Potem powinienem to przetestować:
	- w obrębie tej samej warstwy np. UI, czyli tworzę kolejną instancję browsera i sprawdzam czy ilość produktów została pomniejszona o jeden
	- w obrębie różnych warstw: UI - API - DB

Ważne żeby testów cross-checkingowych nie robić gdzie tylko się da, bo to wydłuża znacząco testy i sprawia, że są mniej niestabilne. Takie testy powinny raczej stanowić dodatek do test suita.

Error conditions
Performance characteristics

## III. Inne dobre praktyki
1. Ograniczyć testy UI dzięki używaniu skrótów w aplikacji - wywoływaniu odpowiednich metod+endpointów API na poszczególnych etapach testów
>https://testautomationu.applitools.com/setting-a-foundation-for-successful-test-automation/chapter3.html
>https://angiejones.tech/hybrid-tests-automation-pyramid/
2. Współpracować z developerami, komunikować im, żeby robili IDki dla webelementów itp.

## Źródła:
- https://app.pluralsight.com/library/courses/test-automation-java-fundamentals/recommended-courses