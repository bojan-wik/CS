#java 

##### Interface w Java:
- zestaw metod (sygnatur metod) bez ich implementacji - bez ich body/kodu, który definiowałby ich sposób działania
- właściwe body metod danego interfejsu znajduje się w klasie implementującej dany interfejs (keyword *implements*)
- jeżeli w interfejsie chcemy metodę z implementacją to musimy zadeklarować ją z keywordem `default`
- w jednej klasie możemy zaimplementować więcej niż jeden interfejs (*multiple inheritance*)
- interfejsy, tak jak klasy, definiujemy w osobnych plikach 
- Interfejsy osiągają 100% poziom abstrakcji 
- nie można tworzyć instancji interfejsu

##### Przykład: 
Plik 'CentralTraffic.java' jest plikiem typu interfejs, który definiuje zestaw metod - reguł ruchu drogowego, które muszą być takie same na całym świecie 
```java
public interface c_Interface_CentralTraffic {

    public void greenGo();
    public void redStop();
    public void flashYellow();
}
```
Plik 'EuropeTraffic.java' jest także interfejsem, ale definiującym reguły ruchu drogowego w obrębie Europy
```java
public interface c_Interface_EuropeTraffic {

    public void europeanTrafficRule();
}
```

Plik 'PolishTraffic.java' jest plikiem typu klasa, który implementuje jednocześnie dwa interfejsy: CentralTraffic + EuropeTraffic, jako że Polska jest krajem, który leży w Europie a szerzej - na świecie.

W pliku tym zdefiniowane są body dla metod, wskazanych w interfejsie. Musi on zawierać wszystkie metody z interfejsu (uniwersalne reguły ruchu drogowego na całym świecie i w Europie), dodatkowo może zawierać swoje własne, lokalne metody (odzwierciedlające lokalne reguły ruchu drogowego w Polsce). 

```java
public class c_Interface_PolishTraffic implements c_Interface_CentralTraffic, c_Interface_EuropeTraffic {

    @Override
    public void greenGo() {
        System.out.println("greenGo interface implementation");
    }

    @Override
    public void redStop() {
        System.out.println("redStop interface implementation");
    }

    @Override
    public void flashYellow() {
        System.out.println("flashYellow interface implementation");
    }

    public void redAndYellow() {
        System.out.println("redAndYellow local implementation");
    };

    @Override
    public void europeanTrafficRule() {
        System.out.println("europeanTrafficRule implementation");
    }

    public static void main(String[] args) {
        c_Interface_CentralTraffic pl = new c_Interface_PolishTraffic();
        pl.redStop();
        pl.flashYellow();
        pl.greenGo();

        c_Interface_PolishTraffic plLocal = new c_Interface_PolishTraffic();
        plLocal.redAndYellow();

        c_Interface_EuropeTraffic plEU = new c_Interface_PolishTraffic();
        plEU.europeanTrafficRule();
    }
}
```