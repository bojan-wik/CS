# Git

## Konfiguracja

Otwarcie config file (global)
```
git config --global -e
```

Ustawienie Notepad++ jako defaultowego edytora
```
git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
```

Ustawienie jak Git powinien traktować *end of lines* (dla Windows)
```
git config --global core.autocrlf true
```
Jest to ważne w przypadku, kiedy nad tym samym kodem pracują ludzie w innych systemach operacyjnych. Windows i MacOS/Linux traktują EOL inaczej, a to ustawienie sprawia, że te różnice są niwelowane

## Workflow

![[Pasted image 20220121145455.png]]

1. working directory - folder z projektem na dysku lokalnym
2. staging area - etap pośredni, trafiają tam zmodyfikowane pliki, które proponujemy do najbliższego commita
3. local repository - folder .git wewnątrz working directory
4. remote repository - projekt w repozytorium online np. GitHub, BitBucket itp.

dysk lokalny -> staging area -> commit -> repozytorium


## Komendy

Sprawdzenie na którym jestem obecnie branchu
```
git branch
```

Zmiana brancha na 'develop'
```
git checkout -b develop
```

Zaciągnięcie najświeższych zmian z brancha 'develop'
```
git pull origin develop
```

---
* https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.htm
* https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/How-to-set-Notepad-as-the-default-Git-editor-for-commits-instead-of-Vim
* https://www.youtube.com/watch?v=8JJ101D3knE
* https://support.atlassian.com/bitbucket-cloud/docs/configure-your-dvcs-username-for-commits/