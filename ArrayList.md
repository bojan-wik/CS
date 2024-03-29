#java 

#### Co to jest?
ArrayList to podstawowa implementacja interfejsu [[List]] w Javie, używana do przechowywania elementów. 

```java
private static final ArrayList<String> groceryList = new ArrayList<String>();
```

W odróżnieniu od [[Array]], która ma charakter statyczny, ArrayList ma charakter dynamiczny - jej implementacja bazuje na tablicy, która jest powiększana wraz ze wzrostem rozmiaru listy. Możemy ją dowolnie powiększać i pomiejszać.
Dzięki temu, jest to najwydajniejsza implementacja [[List]] w Javie (w bibliotece standardowej).

Charakteryzuje się szybkim losowym dostępem do poszczególnych elementów poprzez metodę `get(int index)`.

```java
groceryList.get(1);
```

#### Array vs ArrayList

![[Pasted image 20220602084020.png]]

Jak wspomniane na grafice wyżej - ArrayList, w odróżnieniu od [[Array]] nie jest w stanie przechowywać [[Primitive Data Types]]. Aby to było możliwe trzeba użyć [[Autoboxing and Unboxing]].


#### Convert `ArrayList<String>` to `String[]`
```java
String[] array = {"Arizona", "CA", "NY", "Nevada"};
ArrayList<String> filteredArrayList = new ArrayList<>();

filteredArrayList.toArray(new String[filteredArrayList.size()])
```
>https://www.geeksforgeeks.org/convert-an-arraylist-of-string-to-a-string-array-in-java/

#### Convert `ArrayList<Integer>` to `int[]`
```java
ArrayList<Integer> numbersList = new ArrayList<>();  
int[] array = numbersList.stream().mapToInt(i -> i).toArray();
```
>https://stackoverflow.com/a/23688547