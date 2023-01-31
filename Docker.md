#tools 

**Docker**  to narzędzie do uruchamiania tzw. kontenerów, czyli odizolowanych środowisk programistycznych. Taka konteneryzacja oznacza sposób, w jaki można dostarczyć aplikację ze wszystkimi potrzebnymi dependencjami i wybranym systemem operacyjnym.

Kontenery tworzone są za pomocą obrazów (images). Image kontenera zawiera wszystko co jest potrzebne do uruchomienia aplikacji:
- kod aplikacji,
- środowisko,
- dependencje, biblioteki, narzędzia,
- ustawienia etc.

Kontenery stanowią alternatywę dla [[Virtual Machines]], ale są od nich szybsze, bo nie wymagają postawienia całego systemu operacyjnego.

Zalety konteneryzacji:
- łatwość tworzenia oraz powtarzalność środowisk developerskich,
- uproszczenie procesu dostarczania gotowych aplikacji na docelowe środowiska,
- możliwość eksperymentowania z różnymi wersjami oprogramowania.

##### The current user is not in the 'docker-users' group. Add yourself to the 'docker-users' group and then log out and back in to Windows.

W przypadku takiego errora:
1. Uruchomić Command Prompt z uprawnieniami admina
2. Puścić komendę
```
net localgroup docker-users "DOMAIN\your-user-id" /ADD
```

`your-user-id` to local Windows user name, który można określić patrząc w `C:\Users\`

>https://stackoverflow.com/questions/61530874/docker-how-do-i-add-myself-to-the-docker-users-group-on-windows-10-home


#### Docker is not starting
Pomogło zaktualizowanie kernela WSL2 Linux z:
https://learn.microsoft.com/en-gb/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package

## Źródła:
- https://testautomationu.applitools.com/scaling-tests-with-docker/
- https://www.youtube.com/watch?v=pTFZFxd4hOI