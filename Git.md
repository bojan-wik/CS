#tools 

## I. Pojęcia

1. Branch - pointer, który wskazuje na ostatni commit z serii commitów
2. HEAD - plik w folderze .git, który wskazuje który lokalny branch jest w danym momencie active

Pliki mogą być w trzech różnych stanach:
- untracked - nowe plik, które nie są jeszcze trackowane
- unstaged - pliki, które są już trackowane, ale zostały w międzyczasie zmodyfikowane
- staged - pliki gotowe do zacommitowania

![[Pasted image 20221109152946.png]]

## II. Workflow

![[Pasted image 20220121145455.png]]

1. working directory - folder z projektem na dysku lokalnym
2. staging area - etap pośredni, trafiają tam zmodyfikowane pliki, które proponujemy do najbliższego commita
3. local repository - folder .git wewnątrz working directory
4. remote repository - projekt w repozytorium online np. GitHub, BitBucket itp.

### Przykład użycia
1. Pracuję nad taskiem na własnym kompie, w ramach którego modyfikuję 3 pliki
2. Kończę pracę nad taskiem i chcę go zakomitować do repozytorium. Tworzenie commita to takie jakby robienie snapshota projektu, który prezentuje stan projektu w danym momencie
a)  za pomocą komendy *git add* dodaję zmodyfikowane pliki do *staging area*
b)  w *staging area* dokonuję review zmian, których dokonałem i jeżeli wszystko jest OK to mogę przejść do zrobienia *commita*
3. za pomocą komendy *git commit* kopiuję snapshot projektu (zawierającego 3 zmodyfikowane pliki) ze *staging area* do *local repository* **Ważne**: *staging area* nie jest opróżniane
4. za pomocą komendy *git push* przesyłam snapshot z *local repository* do *remote repository*


## III. Komendy

##### Inicjalizowanie repo lub zaciąganie już istniejącego repo
```
$ git init
$ git clone <url>
```

### 1) fetch + merge = pull

##### Zaciągnięcie najświeższych zmian bez auto-merge (remote repo -> local repo)
```
$ git fetch origin develop
```

#### Mergowanie zmian (local repo -> working dir)
```
$ git merge
```

##### Zaciągnięcie najświeższych zmian z auto-merge (remote repo -> working dir)
np. z brancha 'develop'
```
$ git pull origin develop
```
pull = fetch + merge

![[fetch merge.png]]

### 2) status -> add / stash / remove -> commit

##### Aktualny status (różnice pomiędzy: working dir <-> staging area <-> local repo <-> remote repo)
```
$ git status
```

##### Usuwanie plików, które są untracked
```
$ git clean -df
```

##### Usuwanie plików, które są unstaged
```
$ git checkout -- .
```
>https://www.baeldung.com/git-discard-unstaged-changes

##### Dodanie plików do staging area (working dir -> staging area)
```
$ git add --all
$ git add .
```

##### Usuwanie plików ze staging area (working dir -> staging area)

```
$ git reset HEAD -- path/to/file
```

Od git --version v2.24.0

```
$ git restore --staged <fileName>
```

##### Dodanie plików do stasha (working dir -> stash list)
Czyli np. mam jakieś zmiany, potrzebuję zrobić pulla, nie chcę tych zmian commitować, ale też nie chcę ich tracić. Wtedy mogę je zastashować, tak jakby odłożyć na później
```
$ git stash
```
Wyprintowanie stash list - ostatni stash trafia na górę listy
```
$ git stash list
```
Przywrócenie ostatniego stasha do working dir
```
$ git stash pop
```

##### Zakomitowanie plików (staging area -> local repo)
```
$ git commit -m "nice commit"
$ git commit -am "nice commit directly to local repo"
```
jeżeli chcę zakomitować z pominięciem staging area (working dir -> local repo) dodaję flagę -a

##### Historia commitów
```
$ git log
$ git log --oneline
```

### 3) push

##### Wrzucenie zmian (local repo -> remote repo)
```
$ git push origin master
```

##### Wrzucenie zmian kiedy nie mam jeszcze utworzonego remote repo
```
$ git push --set-upstream origin <nazwa brancha którego tworzymy na remote repo>
albo
$ git push -u origin <nazwa brancha którego tworzymy na remote repo>
```

##### "Pusty" push żeby przetestować połączenie/uprawnienia
>
https://stackoverflow.com/a/73898031

### 4) branch

##### Sprawdzenie na którym jestem obecnie branchu
```
$ git branch -vv
$ git branch -la
```
flaga -vv pokazuje dodatkowo z którym branchem w remote repo jest połączony

##### Utworzenie nowego brancha
```
$ git branch <branchName>
$ git checkout -b <branchName>
```

##### Utworzenie nowego local-brancha i zepnięcie go z remote-branchem
```
$ git checkout -b <my_new_branch> origin/<branch_name>
```
>https://stackoverflow.com/a/11356470

##### Zepnięcie już istniejącego akywnego local-brancha z remote-branchem
```
$ git branch -u origin/<branch_name>
```
>https://www.git-tower.com/learn/git/faq/track-remote-upstream-branch

Czasem zdaża się, że zamiast spiąć z poprawnym remote-branchem spina nam z niepoprawnym np. release albo development. Wtedy najprawdopodobniej musimy zaciągnąć aktualną listę remote-branchy i po puszczeniu tej komendy powinno już poprawnie spinać

```
$ git remote update
```
>https://stackoverflow.com/a/12320286

##### Usunięcie brancha
```
$ git branch -d <branchName>
```

##### Zmiana nazwy aktywnego local-brancha
```
$ git branch -m <newBranchName>
```

##### Zmiana nazwy remote-brancha
>https://www.ionos.com/digitalguide/websites/web-development/renaming-a-git-branch/

##### Zmiana brancha 
```
$ git checkout <branchName>
```

### 4.1) Mergowanie dwóch branchy i rebase

#### a) Merge (fast forward) - w sytuacji kiedy jeden branch tylko 'wyprzedził' drugiego brancha

```
$ git merge <nazwa brancha którego chcemy domergować>
```

##### Przykład:
![[merge fast-forward.png]]
- w tej sytuacji MyNewBranch wyprzedził mastera
- chcę domergować MyNewBranch do master
- robię `$ git checkout master` 
- potem `$ git merge MyNewBranch`
- i pewnie kasuję domergowanego brancha za pomocą `git branch -d MyNewBranch`


#### b) Rebase - w sytuacji kiedy branche się 'rozjechały' i ich ostatnie commity są inne

```
$ git rebase <nazwa brancha którego chcemy domergować>
```

##### Przykład,
przed:
![[rebasing before.png]]
- w tej sytuacji MyNewBranch odbił się od mastera
- jednocześnie rozwijany był MyNewBranch, jak i master i oba mają inne ostatnie commity
- wspólnym parent commitem dla obu branchy jest w tym przypadku commit C
- będąc na MyNewBranch chcę mieć dostęp do najświeższej wersji mastera (commit D)
- robię `$ git checkout MyNewBranch`
- potem `$ git rebase master`

po:
![[rebasing after.png]]
- w momencie rebasingu Git kopiuje commit E do commit E' i potem stawia commit E' za ostatnim commitem z mastera - ==bazujemy na aktualnym stanie gałęzi master, ale nie na samej gałęzi master==
- dzięki rebase możemy integrować zmiany które zachodzą na branchu master z naszym branchem, a na końcu, gdy praca jest skończona możemy użyć fast-forward merge
- rebase pozwala uporządkować historię commitów danego brancha bez dodawania niepotrzebnych merge commitów

### 4.2) Przepisywanie historii brancha

- W obu przypadkach tworzony jest nowy commit z nowym hashem, ale jego timestamp i autor pozostają takie same.
- Złotą zasadą jest żeby przepisywać historię tylko swoich lokalnych branchy, nie robić tego na masterze.

#### a) Amend - nadpisanie ostatniego commita

```
$ git add <new files>
$ git commit --amend
```

#### b) Rebase interactive

```
$ git rebase -i HEAD~3
```
HEAD~3 znaczy kiedy chcę zedytować ostatnie 3 commity

### 5. Cherry Picking
- to kopiowanie commita/ów z jednego brancha do drugiego brancha
- tworzony jest zupełnie nowy commit z nowym hashem, ale z oryginalnym autorem i datą utworzenia

```
$ git cherry-pick <commitHashCode> <commitHashCode>
```

**Przykład**,
przed:
![[Pasted image 20221208090314.png]]
- mamy 3 branche, 'MyNewBranch' jest aktywnym branchem
- chcemy mieć plik index.html w 'MyNewBranch'
- robimy `$ git cherry-pick <u2mvqee>`

po:
![[Pasted image 20221208090716.png]]

Skąd wziąć hashCode commita?
- z remote repo - szukam commit, który chcę przekopiować i kopiuję jego hashCode
- z klienta Gita w IntelliJ

![[Pasted image 20221208093528.png]]

### 6. Resetting
to cofanie commita, które można zastosować dla:
- local repository  (`--soft`)
- staging area (`--mixed`)
- working directory (`--hard`)

#### a) resetting --soft

```
$ git reset --soft HEAD~1
```

**Przykład:**
![[Pasted image 20221213123331.png]]
~1 oznacza o ile commitów cofnąć - w tym przypadku cofamy o 1 commit

#### b) resetting --mixed

```
$ git reset --mixed HEAD~1
```

#### c) resetting --hard

```
$ git reset --hard HEAD~1
```

### 7. Reverting
Is used to revert a specific commit by applying a new commit with the opposite changes.

Czyli coś jak `$ git reset` z tym że commita nie cofamy, tylko tworzymy nowego commita z cofniętymi zmianami.

```
$ git revert <commitHashCode>
```

**Przykład**
![[Pasted image 20221213125604.png]]

Przydatne np. w sytuacji kiedy chcemy =='cofnąć' commit, który został już wypushowany na remote, czyli cofamy commita zarówno na local repo jak i na remote repo==
>https://www.becomebetterprogrammer.com/git-revert-last-commit/

## IV. Commitowanie - najlepsze praktyki

1. Commity powinny być 'w sam raz' - nie za małe, nie za duże tzn. nie ma sensu commitować każdej zmiany, ale też nie ma sensu robić np. tylko jednego commita z wszystkimi zmianami
2. Commity powinny być czymś na wzór checkpointów w grach - ważnych momentów, do których można wrócić
3. Każdy commit powinien reprezentować oddzielny zestaw zmian np.: 
a) napisałem metodę-step testowy -> pierwszy commit
b)  refaktoruję 10 selektorów w innej klasie testowej -> drugi commit
itd.
4. Pisanie sensownych commit messages, które odzwierciedlają sedno zmian

## V. Konfiguracja

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

## VI. Napotkane problemy

##### "The remote end hung up unexpectedly" podczas git pull
>https://stackoverflow.com/a/45117156

## Źródła:
* https://www.youtube.com/watch?v=8JJ101D3knE (30:30)
- https://testautomationu.applitools.com/git-tutorial/