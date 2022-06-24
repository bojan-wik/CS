# Collections
#java 

Java Collections: 
-   framework that provides an architecture to store and manipulate the group of objects. 
-   Can achieve all the operations that you perform on a data such as searching, sorting, insertion, manipulation and deletion 
    

Java Collection means a single unit of objects. 

Java Collection framework provides many interfaces (Set, List, Queue, Deque) and classes (ArrayList, Vector, LinkedList, PriorityQueue, HashSet, LinkedHashSet, TreeSet) 

Collections: 
1.  List (interface) ([code example 1](https://github.com/bojan-wik/SeleniumWithJavaCourse/blob/master/src/Chapter32/ArrayListDemo.java)) 
    -   Ordered collection of objects       
    -   can contain duplicate elements         
    -   Implemented by the classes: ArrayList, LinkedList, Vector, Stack 
        
2.  Set (interface) ([code example 2](https://github.com/bojan-wik/SeleniumWithJavaCourse/blob/master/src/Chapter32/HashSetExample.java))     
    -   unordered collection of objects         
    -   can not contain duplicate elements - używamy wtedy kiedy chcemy uniknąć przechowywania zduplikowanych elementów         
    -   implemented by the classes: HashSet, LinkedHashSet, TreeSet 
        
3.  Map (interface)     
    -   object that maps keys to values         
    -   can not contain duplicate keys         
    -   implemented by the classes: HashMap, TreeMap, LinkedHashMap etc.         

Hierarchia
![[Pasted image 20220622160204.png]]

[[Binary Search]]

### Collections List Methods
##### Kopiowanie listy
```java
List<Theatre.Seat> seatsCopy = new ArrayList<>(theatre.seats);
```
w tym przypadku dokonujemy tzw. [[Shallow copy]], czyli:
- lista sama w sobie jest nowym, osobnym obiektem
- elementy listy nie są nowymi, osobnymi obiektami - to tylko referencje do tych samych obiektów co w pierwszej liście

![[Pasted image 20220624165756.png]]

Dlatego też jeżeli wpłynę na jakiś element listy poprzez obiekt pierwszej listy (theatre.seats) np. dla elementu seatNumber="A01" ustawię reserved=true to jak wywołam ten element poprzez obiekt drugiej listy to on już będzie miał reserved=true - bo to ten sam obiekt.

##### Sortowanie listy
Ale dlatego, że to są osobne listy to jak posortuję pierwszą, to nie wpłynie to na drugą
```java
(theatre.seats).sort(Collections.reverseOrder());
// albo
Collections.reverse(theatre.seats);
```

##### Shuffle - random order listy
```java
Collections.shuffle(theatre.seats);
```