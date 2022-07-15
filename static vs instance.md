# static vs instance
#java #programming 

Keyword *static* to [[non-access modifier]] w Javie, którego możemy używać dla:
1. [[variable]]
2. [[method]]
3. [[block of code]]
4. [[nested class]]

### static vs instance methods

#### static methods
- Static methods nie mają bezpośredniego dostępu ani do instance methods ani do instance variables.
- W static methods niemożliwe jest używanie keyworda *this*. Dlatego static methods są zazwyczaj używane do operacji, które nie wymagają żadnych danych z instancji klasy.
- Zazwyczaj, kiedy metoda nie używa instance variables, to ta metoda powinna być zadeklarowana jako static.
- ==Aby wywołać static method nie musimy wcześniej tworzyć instancji klasy==, wystarczy:
	- ClassName.methodName()
	- methodName(), tylko w obrębie tej samej klasy


#### instance methods
- Instance methods mają bezpośredni dostęp zarówno do innych instance methods jak i do instance variables + do static methods/variables
- Instance methods należą do instancji danej klasy
- ==Aby wywołać instance method musimy utworzyć wcześniej instancję danej klasy== (keyword *new*)

### static vs instance variables

#### static variables
- Każda instancja danej klasy współdzieli te same static variables -> jeśeli taka static variable jest zmieniona, to będzie to miało efekt na każdą instancję klasy
- Static variables nie są używane zbyt często, przydatne np. dla referencji do obiektu *Scanner*

#### instance variables
- Instance variables należą do instancji danych klas, każda instancja klasy ma swoje własne kopie instance variables
- Dzięki temu każda instancja klasy może mieć przypisane inne wartości do instance variables
- Instance variables są używane w większości przypadków