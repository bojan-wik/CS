# Packages in Java
#java 

## Co to jest?
To sposób na enkapsulację zestawu klas, interfejsów, subpackages. 
- Keyword 'import' np. import package.className 
- Niektórych package nie trzeba specjalnie importować - są one ustawione jako defaultowe/globalne I uruchamiane razem z compilerem np. Java.lang 
- Inne trzeba specjalnie importować, żeby móc z nich korzystać np. Java.util 

## Typy:
- wbudowane (In-built)
- stworzone przez usera (User-defined)

Class A can use the Class B directly by creating object if both of them belongs to the same package  

## Wildcardy (*)

Używanie w imporcie gwiazdki np.
```java
import java.util.*;
```
jest postrzegane raczej jako zła praktyka. Nie wpływa to w zasadzie w ogóle na performance, ale chodzi o to, że taki import (wszystkich klas z danej biblioteki) może 'zabrudzić' nasz namespace i spowodować konflikty w nazwach z klasami stworzonymi przez nas.
>https://tharakamd-12.medium.com/is-it-bad-to-use-wildcard-imports-in-java-1b46a863b2be

---
https://www.geeksforgeeks.org/packages-in-java/
