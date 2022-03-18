# Selenium methods
#selenium 

##### getText()
Wyciąganie tekstu z webelementu, ale działa tylko z webelementami, które nie są ukryte.
Dla ukrytych webelementów muszę użyć `getAttribute("textContent")` np.
```java
assertThat(driver.findElement(By.xpath("//span[@ng-if='!isCustomCaption']")).getAttribute("textContent")).contains("0 file");
```
>https://stackoverflow.com/a/32475546