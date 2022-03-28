# Class vs Object OR Instance vs Reference
#java 

##### Na przykładzie budowania domu/budynku.

- **Klasa** to w tym przypadku blueprint/plan architektoniczny konkretnegu budynku. Na podstawie takiego planu możemy zbudować wiele 'kopii' tego samego budynku.

**Przykład:**
Moi rodzice zanim wybudowali nasz dom kupili jego plan.

- Każdy z tych budynków wybudowanych w ten sposób jest **obiektem** albo **instancją** klasy budynku (zainicjalizowanych za pomocą operatora *new*).

**Przykład:**
Moi rodzice na podstawie zakupionego planu wybudowali nasz dom. Nasz dom był jedną z instancji tej samej klasy, czyli planu architektocznicznego. 10 innych osób na podstawie tego samego planu mogło wybudować swoje 10 domów, czyli 10 osobnych instancji tej samej klasy.

- Każdy pojedyńczy budynek ma swój adres - jakąś fizyczną lokalizację. Ten adres to **referencja** tego budynku.

**Przykład:**
Referencją mojego domu był adres: Poprzeczna.

- Daną referencję można kopiować, ale każda z tych kopii będzie odnosić się zawsze do tego samego obiektu/instancji.

**Przykład**:
Organizuję przyjęcie urodzinowe. Chcę zaprosić 5 przyjaciół. Tworzę zaproszenie - na kartce piszę adres mojego domu. W tym momencie stworzyłem referencję do obiektu/instancji. Kseruję zaproszenie 4 razy i ostatecznie mam 5 zaproszeń. Skopiowałem referencje do obiektu, ale nie sam obiekt. Niezależnie od ilości zaproszeń one zawsze będą kierować do tego samego domu.

```java
public class House {

    private String color;

    public House(String color) {
        this.color = color;
    }

    public String getColor() {
        return color;
    }

    public void setColor(String color) {
        this.color = color;
    }
}
```

```java
public static void main(String[] args) {
        // 1
		House blueHouse = new House("blue");
        House anotherHouse = blueHouse;
        System.out.println(blueHouse.getColor()); // blue
        System.out.println(anotherHouse.getColor()); // blue
		
		// 2
        anotherHouse.setColor("yellow");
        System.out.println(blueHouse.getColor()); // yellow
        System.out.println(anotherHouse.getColor()); // yellow
		
		// 3
        House greenHouse = new House("green");
        // 4
		anotherHouse = greenHouse;
        System.out.println(anotherHouse.getColor()); // green
    }
```
ad 1
![[Pasted image 20220328120226.png]]
ad 2
![[Pasted image 20220328115208.png]]
ad 3
![[Pasted image 20220328115236.png]]
ad 4
![[Pasted image 20220328115254.png]]

==Class -> Object/Instance -> Reference==

- Referencje możemy przekazywać jako parametry do konstruktorów i metod.
- ==W Javie mamy do czynienia ZAWSZE z referencjami== do obiektów w pamięci, niemożliwe jest dostać się do obiektów bezpośrednio. Wszystkie interakcje odbywają się za pomocą referencji.
---
https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/9331916#overview