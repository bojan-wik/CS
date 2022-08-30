# Primitive Data Types
#java 

W Javie mamy 8 primitive data types:
- **int** - liczby całkowite np. `3`
- **byte**
- **short**
- **long**
- **float** - ułamki np. `0.5f`, albo po przecinku np. `0,5`
- **double** - ułamki np. `0.5d`, albo po kropce np. `0.5`
- **boolean** - `true` albo `false`
- **char** - pojedyncze litery np. `A`, `z` 


#### convert char to int
```java
char digitAsChar = '9';
int digitAsInt = digitAsChar - '0'
```
>https://stackoverflow.com/a/46343671

#### float vs double
Oba typy służą do przechowywania ułamków (floating point numbers). Jest pomiędzy nimi ileś różnic, ale ==generalnie lepiej używać *double*== - ma dużo większy zasięg i większą precyzję (więcej cyfr po przecinku), ale jest trochę wolniejszy.
> https://favtutor.com/blogs/java-float-vs-double#:~:text=Size%3A%20Float%20is%20of%20size,the%20sign%20of%20the%20number.