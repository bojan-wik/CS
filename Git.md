# Git
#tools 

## 1. Konfiguracja

##### Otwarcie config file (global)
```
git config --global -e
```

##### Ustawienie username i email - mogą być global albo repository-specific
> https://support.atlassian.com/bitbucket-cloud/docs/configure-your-dvcs-username-for-commits/

##### Ustawienie Notepad++ jako defaultowego edytora
```
git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
```
potem za każdym razem jak dam komendę `git commit` bez sprecyzowanego message to otworzy mi się Notepad++
> https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/How-to-set-Notepad-as-the-default-Git-editor-for-commits-instead-of-Vim

##### Ustawienie jak Git powinien traktować *end of lines* (dla Windows)
```
git config --global core.autocrlf true
```
Jest to ważne w przypadku, kiedy nad tym samym kodem pracują ludzie w innych systemach operacyjnych. Windows i MacOS/Linux traktują EOL inaczej, a to ustawienie sprawia, że te różnice są niwelowane

##### Ustawienie credentiali dla Gita w Windowsie (Authentication failed for)
Control Panel -> Credential Manager -> Windows Credentials -> Generic Credentials

i szukam serwisu, dla którego chcę ustawić/zmienić credentiale.
W moim przypadku to był bitbucket, gdzie miałem wcześniej pewnie nieaktualne hasło i za każdym razem jak pushowałem zmiany, to dostawałem
`fatal: Authentication failed for 'https://bitbucket...'`
>https://stackoverflow.com/a/49125803

## 2. Workflow

![[Pasted image 20220121145455.png]]

1. working directory - folder z projektem na dysku lokalnym
2. staging area - etap pośredni, trafiają tam zmodyfikowane pliki, które proponujemy do najbliższego commita
3. local repository - folder .git wewnątrz working directory
4. remote repository - projekt w repozytorium online np. GitHub, BitBucket itp.

### 2.1. Przykład użycia
1. Pracuję nad taskiem na własnym kompie, w ramach którego modyfikuję 3 pliki
2. Kończę pracę nad taskiem i chcę go zakomitować do repozytorium. Tworzenie commita to takie jakby robienie snapshota projektu, który prezentuje stan projektu w danym momencie
a)  za pomocą komendy *git add* dodaję zmodyfikowane pliki do *staging area*
b)  w *staging area* dokonuję review zmian, których dokonałem i jeżeli wszystko jest OK to mogę przejść do zrobienia *commita*
3. za pomocą komendy *git commit* kopiuję snapshot projektu (zawierającego 3 zmodyfikowane pliki) ze *staging area* do *local repository* **Ważne**: *staging area* nie jest opróżniane
4. za pomocą komendy *git push* przesyłam snapshot z *local repository* do *remote repository*


## 3. Komendy

##### Inicjalizowanie repo lub zaciąganie już istniejącego repo
```
git init
git clone <url>
```

##### Sprawdzenie na którym jestem obecnie branchu
```
git branch -vv
```
flaga -vv pokazuje dodatkowo z którym branchem w remote repo jest połączony

##### Zmiana brancha 
np. na 'develop'
```
git checkout -develop
```

##### Zaciągnięcie najświeższych zmian bez auto-merge (remote repo -> local repo)
```
git fetch origin develop
```

#### Mergowanie zmian (local repo -> working dir)
```
git merge
```

##### Zaciągnięcie najświeższych zmian z auto-merge (remote repo -> working dir)
np. z brancha 'develop'
```
git pull origin develop
```
pull = fetch + merge

![[fetch merge.png]]

##### Aktualny status (różnice pomiędzy: working dir <-> staging area <-> local repo <-> remote repo)
```
git status
```

##### Dodanie plików do staging area (working dir -> staging area)
```
git add --all
```

###### Zakomitowanie plików (staging area -> local repo)
```
git commit -m "nice commit"
```
jeżeli chcę zakomitować z pominięciem staging area (working dir -> local repo) dodaję flagę -a
```
git commit -am "nice commit directly to local repo"
```

##### Wrzucenie zmian (local repo -> remote repo)
```
git push origin master
```

#### Historia commitów
```
git log
```

Cheatsheet
> https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html

## 4. Commiting best practices
1. Commity powinny być 'w sam raz' - nie za małe, nie za duże tzn. nie ma sensu commitować każdej zmiany, ale też nie ma sensu robić np. tylko jednego commita z wszystkimi zmianami
2. Commity powinny być czymś na wzór checkpointów w grach - ważnych momentów, do których można wrócić
3. Każdy commit powinien reprezentować oddzielny zestaw zmian np.: 
a) napisałem metodę-step testowy -> pierwszy commit
b)  refaktoruję 10 selektorów w innej klasie testowej -> drugi commit
itd.
4. Pisanie sensownych commit messages, które odzwierciedlają sedno zmian

---
* https://www.youtube.com/watch?v=8JJ101D3knE (30:30)