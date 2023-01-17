#programming #java 

Mechanizm, dzięki któremu jedna klasa może uzyskać dostęp do memberów (fields and [[methods]]) innej klasy.

field = state
method = behaviour

W Javie nie występuje [[multiple inheritance]]. Pojedyńcza klasa może dziedziczyć tylko po jednej klasie.

**Ograniczenia w dziedziczeniu**:

1. Konstruktory ([[Constructor]]) nie są dziedziczone - konstruktory technicznie nie są memberami danej klasy, stąd też nie mogą zostać odziedziczone
2. Private members (fieldy i metody) nie są dziedziczone