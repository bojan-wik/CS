# Java Generics
#java 

#### Co to jest?
**Java Generics** (typy generyczne) - elementy pozwalające pisać kod w Javie bez wskazywania konkretnych typów danych, na których ten kod będzie operował.

W zależności od przekazywanego parametru możemy zmieniać zachowanie obiektu np. w listach, które w zależności od przyjmowanego parametru agregują konkretny typ danych, tzw. *parametrized types*. 
Listy bez sprecyzowanego w parametrze typu danych to tzw. *raw types* - cały czas można je pisać, ale nie jest to zalecane.

#### Korzyści
- możliwość tworzenia bardziej elastycznego i zwięzłego kodu
- kontrola typów na poziomie kompilacji/budowania (pisania w edytorze), a nie dopiero w trakcie uruchomienia programu
- przydatne w implementacji list, wielu algorytmów

