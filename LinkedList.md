#java

#### Co to jest?
Klasa implementująca interfejs [[List]], służąca do przechowywania elementów.
LinkedList to podwójnie powiązana lista. Każdy element tej listy jest osobnym obiektem, który posiada referencję do poprzedniego i następnego elementu listy.

Implementacja ta pozawala dodawać i usuwać elementy w stałym czasie (dodawanie elementu w dowolnym miejscu listy jest bardzo szybkie), ale losowy dostęp do elementów jest sekwencyjny (żeby dostać się do odpowiedniego elementu, trzeba iterować po elementach listy).

#### ArrayList vs LinkedList
LinkedList, tak samo jak [[ArrayList]] implementuje intefejs [[List]] dlatego też dysponuje tym samym zestawem metod. Obie klasy są do siebie podobne i mogą być używane w ten sam sposób, ale zbudowane są inaczej.

* ArrayList - oparta na tablicy, dzięki czemu jest bardziej wydajna.

![[Pasted image 20220602113049.png]]

* LinkedList - przechowuje elementy w specjalnych kontenerach/nodach. LinkedList ma linka do pierwszego kontenera, pierwszy kontener do drugiego itd. Wraz ze zwiększeniem liczby elementów w liście znacząco wzrasta też zużycie pamięci, przez co lista jest o wiele mniej wydajna.

![[Pasted image 20220602113102.png]]

Większość operacji wykonywanych na listach to dodawanie i odczytywanie. Jeśli chodzi o dodawanie elementów do ArrayList, to jest ono tak samo wydajne jak w LinkedList, gdy dodajemy elementy na końcu listy. Co właściwie ma miejsce w większości przypadków. W uproszczeniu możemy przyjąć, że pod tym względem obie listy są równoważne.

==Generalnie jeśli ma się jakieś wątpliwości jakiej listy używać, można zawsze skorzystać z ArrayList, która sprawdza się w 99,9% przypadków.==

---
https://nullpointerexception.pl/dlaczego-zawsze-powinienes-uzywac-arraylist-w-javie/#:~:text=G%C5%82%C3%B3wna%20r%C3%B3%C5%BCnic%C4%85%20pomi%C4%99dzy%20tymi%20listami,jest%20o%20wiele%20bardziej%20pami%C4%99cio%C5%BCerna.
https://www.w3schools.com/java/java_linkedlist.asp