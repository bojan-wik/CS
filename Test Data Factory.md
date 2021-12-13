# Test Data Factory

## Cel

Używanie [[fixed data]] w testach automatycznych jest uważane za złą praktykę i nie powinno się tego stosować.

Dobrze zaimplementowane Test Data Factory pozwala na generowanie i optymalne zarządzanie danymi testowymi w testach automatycznych, co z kolei sprawia z  że sam framework jest łatwiejszy w utrzymaniu.

## Implementacja:
1. Stworzenie klasy do modelowania danych, których potrzebujemy w teście
2. Stworzenie  [[builder class]]
3. Stworzenie [[factory class]] do konsumowania danych
4. Zmodyfikowanie klasy, aby generowała dynamiczne dane
5. Użycie [[factory class]] w teście

---
http://www.eliasnogueira.com/test-data-factory-why-and-how-to-use/
