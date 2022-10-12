# switch statement
#java 

*switch statement* to obok [[if statement]] i [[if-else statement]] jeden z typów [[Selection statements]] w Javie. Używamy go w momencie kiedy chcemy porównać jakąś zmienną warunkową ze zdefiniowanymi wartościami i na podstawie takiego porównania wykonać określony blok kodu.
Możemy używać tu także [[break and continue statemets]]

*switch* działa ze zmiennymi typu:
* [[int]]
* [[byte]]
* [[short]]
* [[long]]
* [[enum]]
* [[String]]

Przykład:
```Java
public class BasicCalculator {  
  
    public static int calculator(int num1, char operator, int num2) {  
  
        int calculationResult = 0;  
 		switch(operator) {  
            case '+':  
                calculationResult = num1 + num2;  
 				break; 
			case '-':  
                calculationResult = num1 - num2;  
 				break; 
			case '*':  
                calculationResult = num1 * num2;  
 				break; 
			case '/':  
                switch(num2) {  
                    case 0:  
                        break;  
 					default:  
                        calculationResult = num1 / num2;
            default:
	            throw new IllegalStateException("No such option in switch statement");`  
 	}  
        }  
        return calculationResult;  
 }  
  
    public static void main(String[] args) {  
        System.out.println(calculator(25, '/', 0));  
 }  
}
```

## switch vs if-else-if

1. Jakie wyrażenie jest testowane?
* if-else-if może testować m.in. zakresy wartości, warunki logiczne np. `score > 60`
* switch może testować tylko pojedyncze integery, Stringi, czy są równe jakiejś wartości np. `case 60`
2. Switch jest lepszy w przypadku multi-way branching

---
https://www.geeksforgeeks.org/switch-statement-in-java/
https://www.geeksforgeeks.org/switch-vs-else/