#tools

## Opcje
Jak wymusić multi-line formatting
>File -> Settings -> Editor -> General -> Code Folding -> 
>Java,  One-line methods: off

Konfiguracja Git
>File -> Settings -> Version Control -> Git
>Path to Git Executable: C:\Program Files\Git\bin\git.exe

Konfiguracja terminala (na BASH)
>File -> Settings -> Tools -> Terminal
>Application settings, Shell path: C:\Program Files\Git\bin\bash.exe

Wyłączenie spellcheckingu
>File -> Settings -> Editor -> Inspections > Proofreading 
>Typo: off

Inne przydatne opcje
>Editor -> General -> Auto import
>Add unambigous imports on the fly: off

Ustawienie klawiszy do przełączania się pomiędzy tabami
>File -> Settings -> Keymap
>Main Menu -> Window -> Editor Tabs
>Select next tab, Select previous tab

## Skróty klawiszowe

Zakomentowanie/odkomentowanie bloku kodu
>ctrl + /
>crtl + shift + /

Wyszukiwanie we wszystkich plikach w projekcie
>ctrl + shift + f

Szukanie wszędzie
>shift shift

Przechodzenie po miejscach, które się odwiedzało
>alt + left
>alt + right

Generowanie kodu
>alt + insert

Zaznaczanie poszczególnych słów
>ctrl+shift+left/right

Wywołanie podpowiedzi jakie parametry są wymagane w danej funkcji
> ctrl + p

## Inne

Żeby terminal w IntelliJ zapamiętywał historię trzeba przed zamknięciem samego IntelliJ zamknąć osobno terminal komendą `$ exit`
>https://intellij-support.jetbrains.com/hc/en-us/community/posts/360002482980/comments/360002321879

### Odpalanie sparametryzowanych testów

W przypadku kiedy test do poprawnego działania potrzebuje dostać jakiś parametr np.
```java
public WebDriver getWebDriverViaParameter() {  
    String browser = System.getProperty("browser").toLowerCase();  
    System.out.println("Running tests in browser: " + browser);  
    return getWebDriver(browser);  
}
```
musimy mu go przekazać (w tym przypadku parametr "browser").

Możemy taki test odpalić w terminalu za pomocą komendy maven
```
$ mvn test -Dbrowser="chrome"
```

albo bezpośrednio w IntelliJ

![[Pasted image 20221202095305.png]]