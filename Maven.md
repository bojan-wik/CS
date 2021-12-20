# Maven

Odpalanie pojedynczego testu, który ma @Tag("test1")
```bash
mvn clean install -Dtag=test1 -Dheadless=N -Djunit.jupiter.execution.parallel.config.fixed.parallelism=1
```