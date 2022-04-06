# Encapsulation
#programming #java 

**Enkapsulacja** - mechanizm, który pozwala na ograniczanie dostępu do poszczególnych komponentów w tworzonych obiektach.
Dzięki temu możemy chronić poszczególne membery danej klasy przed ingerencją 'z zewnątrz'

Generalnie w zdecydowanej większości przypadków zaleca się stosować enkapsulację. Jest to dobrą praktyką.

#### przykład klasy (Player) bez enkapsulacji 
```java 
public class Player {  
  
 public String name;  
 public int health;  
 public String weapon;  
  
 public void loseHealth(int damage) {  
 this.health = this.health - damage;  
 if (this.health <= 0) {  
 System.out.println("Player knocked out");  
 // Reduce number of lives remaining for the player  
 }  
 }  
 public int healthRemaining() {  
 return this.health;  
 }  
}
```
```java
public class Main {  
  
 public static void main(String[] args) {  
 Player player = new Player();  
 player.name = "Forwe";  
 player.health = 20;  
 player.weapon = "Morgenstern";  
  
 int damage = 10;  
 player.loseHealth(damage);  
 System.out.printf("Remaining health = %d", player.healthRemaining()).println();  
  
 damage = 11;  
 player.loseHealth(damage);  
 System.out.printf("Remaining health = %d", player.healthRemaining());
 }  
}
```

#### przykład klasy (Player) z enkapsulacją
```java
public class EnhancedPlayer {  
  
 private String name;  
 private int health = 100;  
 private String weapon;  
  
 public EnhancedPlayer(String name, int hitPoints, String weapon) {  
 this.name = name;  
 if (hitPoints > 0 && hitPoints <= 100) {  
 this.health = hitPoints;  
 }  
 this.weapon = weapon;  
 }  
  
 public void loseHealth(int damage) {  
 this.health = this.health - damage;  
 if (this.health <= 0) {  
 System.out.println("Player knocked out");  
 // Reduce number of lives remaining for the player  
 }  
 }  
 public int getHealth() {  
 return health;  
 }  
}
```
```java
public class Main {  
  
 public static void main(String[] args) {  
  
 EnhancedPlayer enhancedPlayer = new EnhancedPlayer("Victorious", 50, "Axe");  
 System.out.printf("Initial health is %s", enhancedPlayer.getHealth()).println();  
 }  
}
```

---
https://www.udemy.com/course/java-the-complete-java-developer-course/learn/lecture/3323752#overview
https://github.com/bojan-wik/UdemyJavaMasterclass/tree/master/src/encapsulation