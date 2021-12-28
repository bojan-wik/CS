# Maven

Odpalanie pojedynczego testu, który ma @Tag("test_wb")
```bash
mvn clean install -Dtag=test_wb -Dheadless=N -Djunit.jupiter.execution.parallel.config.fixed.parallelism=1
```