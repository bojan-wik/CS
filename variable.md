# Variable
#java #programming 

W Javie można zadeklarować 3 typy zmiennych
1. local variables: 
- zadeklarowane wewn. metod, konstruktorów, albo code bloków
- inicjalizowane tylko wewn. metod i usuwane, gdy wywołanie metody się kończy
2. instance variables: 
- zadeklarowane wewn. klas, ale poza metodami
- inicjalizowane w momencie tworzenia instancji danej klasy
- dostęp do nich można uzyskać z poziomu dowolnej metody/konstruktora/code bloku tej samej klasy
3. class/static variables
- zadeklarowane wewn. klas, ale poza metodami, z keword = static

**Fields** - tak nazywamy zmienne danej klasy, czyli instance variable albo class/static variable

**Properties** - tak nazywamy:
- fields, które mają access modifier = private
- albo metody [[setters]] i [[getters]]