# Maven
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