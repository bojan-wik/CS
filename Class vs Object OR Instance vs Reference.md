# Class vs Object OR Instance vs Reference
#java 

##### Na przykładzie budowania domu/budynku.

- **Klasa** to w tym przypadku blueprint/plan architektoniczny konkretnegu budynku. Na podstawie takiego planu możemy zbudować wiele 'kopii' tego samego budynku.

**Przykład:**
Moi rodzice zanim wybudowali nasz dom kupili jego plan.

- Każdy z tych budynków wybudowanych w ten sposób jest **obiektem** albo **instancją** klasy budynku.

**Przykład:**
Moi rodzice na podstawie zakupionego planu wybudowali nasz dom. Nasz dom był jedną z instancji tej samej klasy, czyli planu architektocznicznego. 10 innych osób mogło nabyć ten sam plan i na jego podstawie wybudować swoje 10 domów, czyli 10 osobnych instancji tej samej klasy.

- Każdy pojedyńczy budynek ma swój adres - jakąś fizyczną lokalizację. Ten adres to **referencja** tego budynku.

**Przykład:**
Referencją mojego domu był adres: Poprzeczna.

- Daną referencję można kopiować, ale każda z tych kopii będzie odnosić się zawsze do tego samego obiektu/instancji.

**Przykład**:
Organizuję przyjęcie urodzinowe. Chcę zaprosić 3 przyjaciół. Przygotowuję 3 zaproszenia, na każdym z nich wypisuję adres mojego domu. W ten sposób skopiowałem referencję. Niezależnie od ilości takich zaproszeń one zawsze będą kierować do tego samego domu. Dom sam w sobie nie byłby kopiowany.

==Class -> Object/Instance -> Reference==

- Referencje możemy przekazywać jako parametry do konstruktorów i metod.
- ==W Javie mamy do czynienia ZAWSZE z referencjami== do obiektów w pamięci, niemożliwe jest dostać się do obiektów bezpośrednio. Wszystko odbywa się za pomocą referencji.

---
https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/9331916#overview