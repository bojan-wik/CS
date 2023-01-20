#programming #java

Java Collections: 
-   framework that provides an architecture to store and manipulate the group of objects. 
-   Can achieve all the operations that you perform on a data such as searching, sorting, insertion, manipulation and deletion 
    

Java Collection means a single unit of objects. 

Java Collection framework provides many interfaces (Set, List, Queue, Deque) and classes (ArrayList, Vector, LinkedList, PriorityQueue, HashSet, LinkedHashSet, TreeSet) 

Collections: 
1.  [[List]] (interface) ([code example 1](https://github.com/bojan-wik/SeleniumWithJavaCourse/blob/master/src/Chapter32/ArrayListDemo.java)) 
    - Ordered collection of objects       
    - can contain duplicate elements         
    - Implemented by the classes: [[ArrayList]], [[LinkedList]], Vector, Stack 
    - dostajemy się do danego elementu poprzez jego pozycję
        
2.  [[Set]] (interface) ([code example 2](https://github.com/bojan-wik/SeleniumWithJavaCourse/blob/master/src/Chapter32/HashSetExample.java))     
    - unordered collection of objects         
    - can not contain duplicate elements - używamy wtedy kiedy chcemy uniknąć przechowywania zduplikowanych elementów         
    - implemented by the classes: HashSet, LinkedHashSet, TreeSet 
    - nie możemy dostać się bezpośrednio do żadnego elementu
        
3.  [[Map]] (interface)     
    - object that maps keys to values
    - unordered collection of objects
    - can not contain duplicate keys         
    - implemented by the classes: HashMap, TreeMap, LinkedHashMap etc.
    - dostajemy się do danego elementu poprzez jego key

Hierarchia
![[Pasted image 20220622160204.png]]

[[Binary Search]]

## Collections List Methods
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

normal order
```java
Collections.sort(theatre.seats);
```
EDIT: Tak napisany statement działa ponieważ wcześniej wewn. klasy *Theatre* zaimplementowałem osobno metodę *compare()*. Gdybym tego nie zrobił statement musiałby wyglądać mniej więcej tak:
```java
Collections.sort(theatre.seats, new Comparator<Seat>) {
	@Override  
	public int compare(Seat seat1, Seat seat2) {  
	    if (seat1.getPrice() < seat2.getPrice()) {  
	        return -1;  
	    } else if (seat1.getPrice() > seat2.getPrice()) {  
	        return 1;  
	    } else {  
	        return 0;  
	    }  
	}
}
```

reverse order
```java
(theatre.seats).sort(Collections.reverseOrder());
// albo
Collections.reverse(theatre.seats);
```

##### Shuffle - random order listy
```java
Collections.shuffle(theatre.seats);
```

#### Min and max value
```java
Theatre.Seat minSeat = Collections.min(theatre.seats);
Theatre.Seat maxSeat = Collections.max(theatre.seats);

System.out.printf("theatre.seats Min seat number is %s", minSeat.getSeatNumber()).println();
System.out.printf("theatre.seats Max seat number is %s", maxSeat.getSeatNumber()).println();
```
Poprawnie wyszukuje min i max value nawet dla nieposortowanych list.

## Code snippets

### Sort List of Strings alphabetically ignore-case
Przykład w [[Lambda Expressions]]

### Sort List of Strings by the length of Strings
```java
List<String> words = Arrays.asList("This", "is", "the", "end");
Collections.sort(words,  
        (word1, word2) -> Integer.compare(word1.length(), word2.length()));
```
>https://edabit.com/challenge/6RStzK9uub9vHDt53
>https://stackoverflow.com/a/35866306

### Źródła:
- https://github.com/bojan-wik/UdemyJavaMasterclass/tree/master/src/section12