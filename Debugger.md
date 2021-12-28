# Debugger

https://www.youtube.com/watch?v=59RC8gVPlvk (14:00)

W czym może pomóc debugowanie?
* znajdowanie i naprawianie bugów
* analiza kodu - jak chcę zrozumieć jakiś fragment kodu, mogę analizować go w głowie, albo odpalić debuggera i zobaczyć linijka po linijce jak działa
* zmiana zachowania aplikacji - poza obserwowaniem wewnętrznego stanu aplikacji mogę go także zmieniać np. poprzez bieżącą zmianę zmiennych i ich wartości
* dodanie logowania 'w locie'
* analiza problemów z pamięcią

Pause Program - pauzuje działanie aplikacji w konkretnym momencie

Po rozwinięciu listy widzę Wątki ([[Threads]]), które w danym momencie działają w aplikacji

![[Pasted image 20211223180229.png]]

Po wybraniu aktualnie działającego thread (w momencie zapauzowania - w tym przypadku jest to thread 'main') widzę jego [[Call Stack]], czyli sekwencję wywołań poszczególnych metod. 
Call Stack jest złożony ze [[Stack Frames]]. Jedno wywołanie metody =  jeden stack frame.

![[Pasted image 20211228123601.png]]

https://www.youtube.com/watch?v=HBlKsk5npWY

1. Breakpoints
2. Watch & Variables
3. The debugging process
4. Evaluate expression
5. Changing values during runtime
6. Common pitfalls