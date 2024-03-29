#tools

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

**Step Over** - egzekucja bieżącej linii kodu i przejście do następnej, bez wchodzenia wewnątrz wywołania metody, jeżeli takie jest obecne w bieżącej linii kodu

**Step Into** - odwrotność Step Over - jeżeli w bieżącej linii kodu jest wywołanie jakiejś metody, to debugger zabierze nas wewnątrz tej metody. Defaultowo debugger nie zabiera nas wewn. metod wbudowanych, tylko do customowych, stworzonych przez nas. Jeżeli chcemy koniecznie wejść wewn. metody wbudowanej musimy użyć **Forced Step Into**

W przypadku kiedy w bieżącej linii kodu mam więcej niż jedno wywołanie metody, wszystkie wywołania są podświetlane i mogę wybrać, które chcę (np. klikając myszką)

![[Pasted image 20211228131805.png]]

**Run to Cursor** - jak nie chce mi się ustawiać breakpoints to mogę kliknąć na linii na której ma się zatrzymać egzekucja kodu i kliknąć opcję Run to Cursor.

**Quick evaluate** - można dokonać ewaluacji pewnych działań w locie. Wciskam klawisz alt i klikam na część kodu, którą chcę zewaluować

![[Pasted image 20211228151252.png]]

**Evaluate expression** - dzięki tej opcji mogę dokonywać ewaluacji valuesów, których nie ma w kodzie źródłowym

![[Pasted image 20211228152713.png]]

**Watches** - istnieje też możliwość dodania valuesów globalnych, których nie ma w kodzie źródłowym (W dialogu Evaluate expression mogę dodawać tylko zmienne lokalne). Robi się to za pomocą dodawania tzw. Watches

![[Pasted image 20220104140828.png]]

**Zmienianie wartości 'w locie'**

![[Pasted image 20220104141237.png]]

**Breakpoint condition** - istnieje możliwość ustalenia warunku w jakim breakpoint ma zadziałać, czyli jeśli:
* warunek jest spełniony - breakpoint zadziała i działanie aplikacji jest wstrzymywane
* warunek nie jest spełniony - breakpoint nie zadziała i tym samym nie zatrzyma działania aplikacji

Prawy klik na breakpoincie
![[Pasted image 20220104142130.png]]
W tym przypadku breakpoint zadziała w momencie kiedy zmienna read jest różna od 10

---
https://www.youtube.com/watch?v=59RC8gVPlvk
https://www.youtube.com/watch?v=HBlKsk5npWY

1. Breakpoints
2. Watch & Variables
3. The debugging process
4. Evaluate expression
5. Changing values during runtime
6. Common pitfalls