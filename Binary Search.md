#java #programming 

to ==algorytm do wyszukiwania danych==, oparty na metodzie 'dziel i zwyciężaj'.

Ogólna zasada działania algorytmu polega na „dzieleniu” listy liczb na połowę i sprawdzaniu czy element znajdujący się dokładnie po środku jest elementem szukanym, jeśli nie to czy jest większy lub mniejszy. W ten sposób bardzo szybko zawężamy zakres poszukiwań, aż w końcu natrafimy na element który poszukujemy lub po prostu go nie znajdziemy.

Algorytm bardziej wydajny od wyszukiwania liniowego/sekwencyjnego (np. for-loop), ale ==wymaga posortowanej listy==.


## Array

```java
// BINARY SEARCH  
public static boolean isDuplicate1(int[] numbers, int searchedNumber) {  
    Arrays.sort(numbers);  
    int index = Arrays.binarySearch(numbers, searchedNumber);  
    if (index >= 0) {  
        return true;  
    } else {  
        return false;  
    }  
}

// LINEAR/SEQUENTIAL SEARCH  
public static boolean isDuplicate(int[] numbers, int searchedNumber) {  
    for (int number : numbers) {  
        if (number == searchedNumber) {  
            return true;  
        }  
    }  
    return false;  
}
```

## Collections

```java
public boolean reserveSeat(String seatNumber) {
        // BINARY SEARCH - bardziej wydajne w tym przypadku (posortowana lista)
        Seat requestedSeat = new Seat(seatNumber);
        int foundSeat = Collections.binarySearch(seats, requestedSeat, null);
        if (foundSeat >= 0) {
            return seats.get(foundSeat).reserve();
        } else {
            System.out.printf("There is no seat %s", seatNumber).println();
            return false;
        }
        // LINEAR SEARCH - mniej wydajne w tym przypadku
//        Seat requestedSeat = null;
//        for (Seat seat : seats) {
//            System.out.print(".");
//            if (seat.getSeatNumber().equals(seatNumber)) {
//                requestedSeat = seat;
//                break;
//            }
//        }
//        if (requestedSeat == null) {
//            System.out.printf("There is no seat %s", seatNumber).println();
//            return false;
//        } else {
//            return requestedSeat.reserve();
//        }
    }
```

## Źródła:
- https://github.com/bojan-wik/UdemyJavaMasterclass/tree/master/src/section12
- https://testautomationu.applitools.com/java-programming-course/chapter7b.html