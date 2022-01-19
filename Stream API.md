# Stream API
#java 

## Overview:
* feature wprowadzony wraz z Java 8
* upraszcza kod
* wykorzystuje/wspiera założenia [[Functional programming]]

## Main features:

* Streamy same w sobie nie są [[data structure]] - nie przechowują danych. Przyjmują tylko jako input różne typy kolekcji danych np. [[Collections]], [[Arrays]] itp.
* Taki przyjęty przez stream input stanowi jego sekwencję elementów na których potem można wykonywać różne operacje, które potem można pipelinować, żeby otrzymać oczekiwany efekt
* Streamy nie modyfikują oryginalnego źródła danych (przyjętego jako input)

## Sposób działania
można podzielić na 3 etapy:
1. Uworzenie streama - przekonwertowanie inputu do streama
2. Zastosowanie *operacji pośrednich* ([[map()]], [[filter()]] albo [[sorted()]])
3. Zastosowanie *operacji kończącej* (np. [[forEach()]], [[count()]], [[collect()]], [[reduce()]])

## Zastosowanie


---
https://geek.justjoin.it/zastosowanie-stream-api-z-java-8-przyklady
https://www.geeksforgeeks.org/stream-in-java/