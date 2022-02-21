# IntelliJ Debugger + Maven tests
#tools

## Problem

Do tej pory debuggowałem standardowo bezpośrednio w IntelliJ.
We frameworku PubCenter testy da się odpalać tylko przez komendy Mavena (w linii komend). Tym samym nie da się tych testów debuggować bezpośrednio w IntelliJ.

## Setup

W IDE, wewnątrz projektu -> Add/Edit Configuration

![[Pasted image 20220104131412.png]]

## Debugging

1. W IDE - dodać breakpointy
2. W terminalu -  wpisać komendę (dla test method z tagiem @Tag="test_wb"):
```
mvnDebug -DforkCount=0 clean install -Dtag=test_wb -Dheadless=N -Djunit.jupiter.execution.parallel.config.fixed.parallelism=1
```
3. W terminalu - poczekać, aż pojawi się komunikat:
`Listening for transport dt_socket at address: 8000`
4. W IDE - kliknąć na Debug button

#### Debuggowanie konretnej test method
```
mvnDebug -DforkCount=0 clean install -Dtest=TestClassName#TestMethodName -Dheadless=N -Djunit.jupiter.execution.parallel.config.fixed.parallelism=1
```

---
https://spin.atomicobject.com/2020/08/20/maven-debugging-intellij/
https://maven.apache.org/surefire/maven-surefire-plugin/examples/debugging.html
