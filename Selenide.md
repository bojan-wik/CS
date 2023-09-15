#selenide

## Code snippets

#### upload file on hidden input

Przypadek, gdzie element input jest ukryty poprzez klasę 'file_input_hidden'. Niemożliwe jest wtedy uploadowanie plików. 

![[Pasted image 20230915124906.png]]

Rozwiązaniem jest usunięcie klasy poprzez skrypt JS:
```java
@Test  
public void uploadFileOnHiddenInput() {  
    CartPage cartPage = homePage.clickShoppingCartButton();    
    executeJavaScript("document.getElementById(\"upfile_1\").classList.remove(\"file_input_hidden\")");  
  
    cartPage  
            .clickSelectFileButton("C:\\Users\\wrbw\\Downloads\\test.txt")  
            .clickUploadButton();  
}
```
>https://youtu.be/MA8QC4Eoaps?si=vqlaETUgUo2c9OqC&t=283