# toString() method
#java 

Metoda toString() jest użyteczna w momencie, kiedy chcemy przedstawić jakiś obiekt jako String.

Metoda toString() jest wbudowana w Javę i uruchamiana jest przez compiler zawsze, kiedy printujemy jakiś obiekt. Ale ta wbudowana metoda nie printuje nam wartości, które mamy w obiekcie, tylko [[hashcode]] obiektu.

I taki kod:
```Java
public class Student {  
  
 private int rollno;  
 private String name;  
 private String city;  
  
 Student(int rollno, String name, String city) {  
    this.rollno = rollno;  
 	this.name = name;  
 	this.city = city;  
 }
 
/*@Override  
public String toString() {  
    return "\nrollno: " + rollno + "\nname " + name + "\ncity: " + city;  
}*/
 
 public static void main(String[] args) {  
 	Student student1 = new Student(1, "Wiktor", "Poznań");  
 	Student student2 = new Student(2, "Zdzichu", "Kraków");  
  
 	System.out.println(student1);  
 	System.out.println(student2);  
 }  
}
```
Wyprintuje nam coś takiego:
```
various.toStringMethod.Student@568db2f2
various.toStringMethod.Student@378bf509
```
Ale po odkomentowaniu tej magicznej linijki i nadpisaniu metody toString():
```Java
@Override  
public String toString() {  
    return "\nrollno: " + rollno + "\nname " + name + "\ncity: " + city;  
}
```
Dostajemy coś takiego:
```
rollno: 1
name Wiktor
city: Poznań

rollno: 2
name Zdzichu
city: Kraków
```

---
https://www.javatpoint.com/understanding-toString()-method