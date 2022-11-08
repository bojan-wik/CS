#tools

Odpalanie testu z konkretnym tagiem @Tag("test_wb")
```
mvn clean install -Dtag=test_wb -Dheadless=N -Djunit.jupiter.execution.parallel.config.fixed.parallelism=1
```

Odpalanie pojedynczej klasy testowej
```
mvn clean install -Dtest=TestClassName -Dheadless=N -Djunit.jupiter.execution.parallel.config.fixed.parallelism=1
```

Odpalanie pojedynczej metody testowej
```
mvn clean install -Dtest=TestClassName#TestMethodName -Dheadless=N -Djunit.jupiter.execution.parallel.config.fixed.parallelism=1
```

Niektóre parametry (np. hasła) mogą zawierać wykrzykniki. Wykrzyknik w bashu stanowi referencję do poprzednio wpisywanych komend. Można to wyłączyć za pomocą
```
set +H
```
>https://serverfault.com/questions/208265/what-is-bash-event-not-found