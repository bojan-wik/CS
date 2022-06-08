# ListIterator
#java #programming 

Interface służący do iterowania po elementach listy w obu kierunkach, do przodu i do tyłu, w odróżnieniu np. od [[Iterator]], gdzie mogę iterować tylko do przodu. ListIterator mogę wykorzystywać np. w [[ArrayList]], [[LinkedList]] itp.

```java
LinkedList<String> cities = new LinkedList<String>();
ListIterator<String> listIterator = cities.listIterator();
```

Ważną rzeczą do zapamiętania jest to, że w ListIterator nie ma czegoś takiego jak aktualny element - 'kursor' zawsze leży w pozycji pomiędzy elementami listy.

![[Pasted image 20220608093619.png]]

Może to prowadzić do sytuacji/problemu, gdzie iterując w przód i w tył po liście nie otrzymujemy takich elementów, jakich byśmy się spodziewali - ponieważ kursor nie znajduje się w 'odpowiedniej' pozycji.

W kursie Tima Buchalki na przykładzie metody, która iteruje po liście miast zostało to rozwiązane poprzez:
- dodanie dodatkowej flagi boolean (goingForward)
- dodanie dodatkowej walidacji (if) przed przechodzeniem w przód/tył

![[Pasted image 20220608111858.png]]

---
https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/3519862#notes
https://github.com/bojan-wik/UdemyJavaMasterclass/blob/master/src/section8/linkedList/Demo.java