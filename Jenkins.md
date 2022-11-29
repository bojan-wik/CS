#tools 

## Co to jest

**Jenkins** – server-based system that helps automate software building, testing and deploying. It facilitates continuous integration and continuous delivery. 

### Przykładowy scenariusz: 

- Mam napisanych 500 test casów. Na mój obecny stan wiedzy mogę je odpalić ręcznie albo za pomocą pliku *.xml, albo za pomocą komendy Maven. 
- Odpalenie wszystkich test casów zajmuje 7 godzin. Gdyby można było tylko odpalać testy ręcznie, odpalenie wszystkich test casów trwałoby przez prawie cały dzień roboczy. 
- Dzięki Jenkins i jego jobs, jestem w stanie zautomatyzować odpalanie testów na dowolną godzinę np. w środku nocy. W przypadku Medcina jest to 1 AM. 

## Instalacja i konfiguracja

### Instalacja (w folderze z plikiem war): 
- java -jar jenkins.war -httpPort=8080 

### Konfiguracja global settings (Manage Jenkins -> Global Tool Configuration) 
- Lokalna ścieżka do JDK, ta sama, jak dla JAVA_HOME w Environmental Variables w systemie: 
`C:\Program Files\Java\jdk1.8.0_241`
- Lokalna ścieżka do Maven

### Konfiguracja workspace, zakładanie projektu/joba 

a) dodanie kodu projektu, możliwe na dwa sposoby: 
- z repozytorium - poprzez podanie odpowiedniego linka np. do repo na GitHub 
- lokalnie – poprzez ustawienie odpowiedniej ścieżki do folderu projektu w 'Use custom workspace' 

b) Build - ustawienia builda przy pomocy Maven 
- wybranie wersji Maven, ustawionej wcześniej w global settings (pkt. 2) 
- Podanie komendy Maven, która uruchamia wykonanie test casów 
`mvn test -PRegression`, gdzie 'Regression' to wartość id podana w pliku 'pom.xml')

c) Post-build Actions – tutaj mogę ustawić, jakie akcje mają zostać wykonane po wykonaniu builda np. Wygenerowanie raportu 

## Źródła:
- https://testautomationu.applitools.com/jenkins-tutorial/