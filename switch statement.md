# switch statement
#java 

*switch statement* to obok [[if statement]] i [[if-else statement]] jeden z typów [[Selection statements]] w Javie. Używamy go w momencie kiedy chcemy porównać jakąś zmienną warunkową ze zdefiniowanymi wartościami i na podstawie takiego porównania wykonać określony blok kodu.

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
 	}  
        }  
        return calculationResult;  
 }  
  
    public static void main(String[] args) {  
        System.out.println(calculator(25, '/', 0));  
 }  
}
```

---
https://www.geeksforgeeks.org/switch-statement-in-java/
https://www.geeksforgeeks.org/switch-vs-else/