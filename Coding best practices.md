#programming 

## Naming conventions

1. **Package**
- nazwa zaczynająca się od małej litery,
- nazwa unikalna
- z reguły składająca się URLa napisanego od końca np.
```
com.roche
com.timbuchalka.autoboxing
```

2. **Class**
- nazwa zaczynająca się od dużej litery,
- pisana camelCase
- będąca rzeczownikiem np.
```
Account, Storage, RequestBody, Response
```

3. **Interface**
- nazwa zaczynająca się od dużej litery,
- pisana camelCase

4. **Method**
* nazwa zaczynająca się od małej litery,
* pisana camelCase,
* z reguły zaczynająca się od czasownika np.
```
getData(), sendData(), fetchUser()
```

5. **Constant** (zmienne typu `static final`)
- nazwa powinna być pisana dużymi literami 
- i z użyciem snake_case np.
```
CONNECTION_LIMIT, POOL_SIZE, BATCH_SIZE
```

6. **Variable**
- nazwa zaczynająca się od małej litery,
- pisana camelCase np.
```
i, minNumber, arrayOfNames
```

7. **Boolean**
* nazwa powinna formułować pytanie
* zaczynać się od "is" np.
```
isValidUser, isOpen, isClosed
```

## Sposoby zapisu:
* snake_case
* camelCase
* PascalCase
* kebab-case

Tylko jeden sposób powinien być używany w całym projekcie. Nie powinno się ich mieszać

---
https://medium.com/@Bigscal-Technologies/a-guide-to-achieve-clean-code-and-best-coding-practices-6b3f0eaa7fa4