# Reference vs Object vs Instance vs Class
#java 

##### Na przykładzie budowania domu/budynku.

1. **Klasa** to w tym przypadku blueprint/plan architektoniczny konkretnegu budynku. Na podstawie takiego planu możemy zbudować wiele 'kopii' tego samego budynku.

**Przykład:**
Moi rodzice zanim wybudowali nasz dom kupili jego plan.

2. Każdy z tych budynków wybudowanych w ten sposób jest **obiektem** albo **instancją** klasy budynku.

**Przykład:**
Moi rodzice na podstawie zakupionego planu wybudowali nasz dom. Nasz dom był jedną z instancji tej samej klasy, czyli planu architektocznicznego. 10 innych osób mogło nabyć ten sam plan i na jego podstawie wybudować swoje 10 domów, czyli 10 osobnych instancji tej samej klasy.

3. dy pojedyńczy budynek ma swój adres - jakąś fizyczną lokalizację. Ten adres to **referencja** tego budynku.

**Przykład:**
Referencją mojego domu był adres: Poprzeczna.

4. Daną referencję można kopiować, ale każda z tych kopii będzie odnosić się zawsze do tego samego obiektu/instancji.

**Przykład**:
Organizuję przyjęcie urodzinowe. Chcę zaprosić 3 przyjaciół. Przygotowuję 3 zaproszenia, na każdym z nich wypisuję adres mojego domu. W ten sposób skopiowałem referencję. Niezależnie od ilości takich zaproszeń one zawsze będą kierować do tego samego domu. Dom sam w sobie nie byłby kopiowany.

5. Referencje możemy przekazywać jako parametry do konstruktorów i metod.