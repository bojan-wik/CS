#programming #java

## this keyword
- używa się go żeby uzyskać dostęp do memberów bieżącej klasy
- jest wymagany w przypadku kiedy parametr danej metody ma taką samą nazwę co zmienna klasy
- powszechnie używany w konstruktorach ([[Constructor]]) i metodach typu *setters*, opcjonalnie w metodach *getters*

```java
public class Person {  
  
    private String name;  
  
    public Person(String name) {  
        this.name = name; 
    }
  
    public String getName() {  
        return name;  
    }  
  
    public void setName(String name) {  
        this.name = name;  
    }
}
```

## super keyword
- używa się go żeby uzyskać dostęp do memberów (zmiennych i metod) super-klasy
- powszechnie używany w przypadku [[Method overriding]], kiedy chcemy wywołać metodę z super-klasy o takiej samej nazwie

```java
class SuperClass {  
  
    public void printMethod() {  
        System.out.println("Printed in Super-class");  
    }  
}  
  
class SubClass extends SuperClass {  
  
    @Override  
    public void printMethod() {  
        super.printMethod();  
        System.out.println("Printed in Sub-class");  
    }  
}  
  
class MainClass {  
  
    public static void main(String[] args) {  
        SubClass subClass = new SubClass();  
        subClass.printMethod();  
    }  
}

/* OUTPUT: 
Printed in Super-class  
Printed in Sub-class  
 */
```

## this() vs super() method calls
opisane w [[Constructor]]

## Źródła:
- https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/9331920#overview