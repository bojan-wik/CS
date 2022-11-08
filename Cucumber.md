#tools 

**Cucumber** to narzędzie, które wykorzystuje [[Behavior Driven Development]] do pisania testów z wykorzystaniem języka [[Gherkin]].

## I. Step Annotations

![[Pasted image 20221107145258.png]]

## II. Feature & .feature file

- **Feature** jest definiowany jako funkcjonalność albo moduł aplikacji, której testy piszemy.
- **.feature** to plik, w którym zapisane są testy Cucumber. Dobrą praktyką jest mieć osobne pliki .feature per feature.

![[Pasted image 20221107150445.png]]

### 1. Scenario
### 2. Scenario Outline
pozwala parametryzować testy

![[Pasted image 20221107150817.png]]

### 3. Background
- Jeżeli mamy step Given wspólny dla więcej niż jednego Scenario, to możemy go wyeksportować do adnotacji Background.
- Step w Background jest uruchamiany przed każdym Scenario, ale po jakimkolwiek hooku Before.

![[Pasted image 20221107151805.png]]

### 4. Tags
### 5. Hooks

![[Pasted image 20221108100217.png]]

## III. Step definitions
- to metoda Java z dodaną odpowiednią adnotacją, która prowadzi do konkretnego stepu w Cucumber
- w momencie wykonywania danego stepu tak naprawdę pod maską wywoływana jest połączona z nią metoda Java

![[Pasted image 20221107153217.png]]

## IV. Best practices
1. Zawsze pisać Scenario z perspektywy endusera
2. Nie skupiać się za bardzo na UI i jego szczegółach, bardziej na flow endusera
3. Unikać użuwania technicznych terminów
4. W danym Scenario powinno być:
- tylko po jednym stepie Given, When, Then
- maksymalnie dwa stepy And
- maks 5 stepów w sumie - jeżeli wychodzi więcej to lepiej jest je rozbić na dwa osobne Scenario

---
https://testautomationu.applitools.com/cucumber-java-tutorial/
