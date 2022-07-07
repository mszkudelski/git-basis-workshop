# Git - praca z lokalnym repozytorium 

## Wstęp

**Potrzeba**:
- Cofnąć się do starszej wersji.
- Połączyć wersje rozwijane przez dwie różne osoby.
- Spojrzeć do historii projektu.
- Znaleźć moment w którym pojawił się błąd w projekcie.

**Problem**: Zapisując pliki na komputerze mamy tylko najnowszą wersję.

**Rozwiązanie**: System kontroli wersji (**V**ersion **C**ontrol **S**ystem)

GIT - najpopularniejszy, obecnie używany system kontroli wersji

Jest to szereg komend do wykorzystania w terminalu, które pomagają zarządzać wersjami projektu.

Istnieją przeróżne narzędzia z interfejsem graficznym, które ułatwiają pracę na nim.


Git to CLI (Command Line Interface). Jest to "przeciwieństwo" interfejsu graficznego. Wszystki operacje wykonuje się w konsoli (wierzu poleceń - command line)

## Nawigacja po katalogach w konsoli

W konsoli/terminalu możemy robić takie same operacje na plikach jak w narzędziu graficznym.

- pwd - print working directory
- mkdir - make directory
- touch - create empty file
- ls - list
- cd <ścieżka> - change directory
- . - obecna ścieżka
- .. - poziom wyżej
- ./project - folder desktop zaczynając od obecnej ścieżki
- ~/ - ścieżka zaczynająca od katalogu domowego
- / - ścieżka absolutna

### Zadanie

1. Otwórz terminal.
2. Sprawdź w jakim katalogu się znajdujesz, jaka prowadzi do niego ścieżka oraz jakie katalogi zawiera.
3. Stwórz katalog "projects", a w nim "git-workshop".
4. Przejdź do tego katalogu.
5. Wyświetl obecną ścieżkę.

jak nawigować po katalogach z poziom terminala
jak operować (CRUD) na katalogach i plikach z poziom terminala

## Konfiguracja Gita

``` bash
git --version # upewniamy się, że mamy Gita
git config --list # pokazuje aktualną konfigurację 

git config --global user.name "Marek Szkudelski"
git config --global user.email "marek@szkudelski.dev"
git config --global core.editor "code --wait"
```

jak skonfigurować Gita (username, email, editor)

## Repozytorium

Główny folder naszego projektu.

Jest kontrolowany całkowicie przez Gita.

Info, które potrzebuje Git jest w ukrytym folderze `.git`.

jak założyć repozytorium lokalne

### Tworzenie repo

Możemy to zrobić na dwa sposoby:
- pobrać istniejące repo
- utworzyć repo w danym folderze

Tworzenie repo od zera:
```bash
git init
```
Wyświetlanie statusu repo:
```bash
git status
```

>Od teraz Git śledzi wszystkie zmiany.

Wyświetlanie konkretnych zmian:
``` bash
git diff
```

### Zadanie
1. We wcześniej utworzonym folderze utwórz repo.
2. Stwórz w nim pusty plik `index.txt`
3. Zobacz jaki jest status repo.
4. Dowolnym sposobem dodaj jakiś tekst do pliku. (Jeśli nie chcesz wychodzić z terminala, to po prostu przeklej `echo "text" >> index.txt`)
5. Sprawdź jakie zmiany wykrył Git.

> **Uwaga!**
>
> Git śledzi zmiany w katalogu, ale to nie oznacza, że są one zapisywane!

## Zapisywanie zmian w repo.

Trzeba zawsze wykonać 2 kroki, żeby zapisać zmiany w repo.

![Proces zapisu zmian](git-process2.png "Proces zapisu zmian")

Working directory - to co aktualnie widzimy w repo, wszystkie niezapisane zmiany

Stating area - zmiany oczekujące na zapisanie

Repository - wszystkie zapisane zmiany

> Ten sam plik może zupełnie inaczej wyglądać w każdym z tych trzech obszarów

> Nawet cały folder może się zupełnie różnić pomiędzy tymi obszarami

TODO wymyśleć dobrzy przykład z życia

Dodanie zmiany do staging area:
``` bash
git add filename

git add . # wszystkie zmiany
```

Dodanie zmiany do repozytorium:
``` bash
git commit # otwiera edytor

git commit -m "opis zmian"
```

Treść opisu commit'a powinna być:
- jasna
- zwięzła

Podglądanie listy commit'ów:
```bash
git log
git log --oneline # pokazuje zwięzłą listę
```

jak i kiedy zapisywać zmiany w repozytorium
jak identyfikować obszary w gicie i do czego one służą (working directory, staging, repository)

### Zadanie

1. Dodaj aktualne zmiany do staging area.
2. Nanieś kolejne zmiany na nasz plik.
3. Sprawdź jaki jest status repo.
4. Zapisz wszystkie zmiany w repo.

## Gałęzie

Branch (gałąź) pomaga prowadzić dwie równoległe historie.

Branch wskazuje na konkretny commit (jest to wskaźnik)

Dwa branche mogą wskazywać na ten sam commit. Wtedy ich historie są identyczne.



``` bash
git branch <nazwa-brancha> #tworzenie brancha
git branch # listowanie branchy

git checkout <nazwa-brancha> # przechodzenie na branch
git checkout -b <nazwa-brancha> # stworzenie i przejście na branch - najprostszy sposób

git checkout - # cofa do ostatniego miejsca
```

Pierwszy branch to `main` lub `master`.

Kolejne branche najczęściej nazywa się:
- develop - wersja, gdzie pracują developerzy i testują testerzy
- feature/opis-zadania - branche do codziennej pracy


![Branches](branches.svg "Branches")

Możemy porównać gałęzie za pomocą:
``` bash
git diff <nazwa brancha>
```

### Zadanie

1. Utwórz gałąź `feature/change`
2. Wykonaj i zacommituj jakąś zmianę
3. Porównaj z branchem `main`

jak i po co zakładać gałęzie i jak się między nimi przełączać

## Wskaźnik HEAD

HEAD wskazuje gdzie aktualnie się znajdujemy. 

HEAD może być tożsamy z danym branchem.

HEAD może wskazywać na dowolny commit w historii - wtedy mówimy o `detached HEAD`

HEAD możemy sprawdzić za pomocą `git log`.


HEAD wskazuje na branch:
![HEAD](head.png "HEAD")


HEAD wskazuje na commit bez brancha:
![Detached HEAD](head2.png "Detached HEAD")

Tworzenie detached HEAD:
```bash
git checkout <hash commita>
```

Naprawianie detached HEAD:
```bash
git checkout <nazwa brancha>

git checkout - # tylko jeśli zrobiliśmy jeden checkout wcześniej
```

Możemy też utworzyć rozgałęzienie z detached HEAD:
```bash
git checkout <hash commita>
git checkout -b <nazwa nowego brancha>
```

![Detached HEAD](head3.png "Detached HEAD")

czym jest detached HEAD

## Łączenie gałęzi

Prędzej czy później musimy scalić dwie osobne wersje projektu.

```bash
git merge <nazwa brancha>
```

```bash
git checkout main
git merge feature/1
```
Mergujemy `feature/1` do `main`, więc na `main` są wszystkie commity z `feature/1`. Ale na `feature/1` mogą nie być wszystkie commity z `main`.

### Zadanie

1. Dociągnij zmiany z `feature/changes` do `main`.
2. Wróć na feature branch.
3. Porównaj teraz te dwa branche.

### Konflikty

Często okazuje się przy merge'u, że historie z dwóch gałęzi się wzajemnie wykluczają.

Do konfliktu dochodzi jeśli ta sama linijka kodu została zmieniona na dwóch gałęziach.

Konfilkty najlepiej rozwiązywać w edytorze.

### Zadanie

1. Utwórz nowy branch z `main`.
2. Utwórz plik `conflict.txt` z treścią `zmiany`
3. Utwórz kolejny branch z `main`.
4. Utwórz plik `conflict.txt` z treścią `inne zmiany`.
5. Spróbuj połączyć te dwie gałęzie.
6. Rozwiąż konflikty w VSC

czym jest merge i jak rozwiązać konflikt

### Łączenie strategią Fast-formard

TODO czym jest fast-forward merge, kiedy zachodzi i jak go uniknąć
