# GIT - praca ze zdalnym repozytorium

## Czym jest zdalne repo

Zdalne repozytorium jest kopią naszego lokalnego i na odwrót.

Mogą się one różnić.

Jest wiele platform, które umożliwiają pracę ze zdalnymi repo - często za darmo.

Github (najpopularniejszy), Gitlab, Bitbucket...

## Co daje zdalne repo

1. Możliwość współpracy z innymi.
2. Kopię zapasową projektu.


## Rozpoczęcie pracy ze zdalnym repo

Są dwie drogi:

1. Utworzenie zdalnego repo i sklonowanie go.

2. Utworzenie lokalnego repo i podpięcie zdalnego repo.

Tak jak robiliśmy to wcześniej (`git init`) + `git add remote`.

> ### Uwaga
>
> Zdalne repo, które podpinamy powinno być puste

```bash
mkdir project
cd project

git init
git add remote origin git@github.com:organizacja/repo.git
```

`origin` jest domyślną nazwą zdalnego repo

> ### Ciekawostka
> 
> Możemy dodać wiele zdalnych repo

Sprawdzenie zdalnych repo:
```bash
git remote -v
```

## Praca z Githubem

Github udostępnia bardzo dużo opcji do zarządzania kodem projektu.

### Tworzenie i klonowanie repo

Przede wszystkim możemy tworzyć i pobierać repozytoria z poziomu Githuba.

Alternatywa do podłączania zdalnego repo:
1. Tworzymy repo w Githubie
2. Klonujemy je. Możemy to zrobić na dwa sposoby - ssh, https (wymaga loginu i hasła)
```bash
git clone <opcjonalna nazwa origina> git@github.com:organizacja/repo.git
```

### Pull Requesty

Główną z nich są Pull Requesty.

Dzięki nim sygnalizujemy chęć domergowania zmian.

Cel:
- komunikacja z zespołem
- wymiana wiedzy
- sprawdzanie kodu (code review)
- uruchomienie procesu sprawdzania kodu

### Edycja plików

Możemy nanosić zmiany i commitować bezpośrednio w Githubie. 

Nie jest to zbyt praktyczne w codziennej pracy.


## Praca ze zdalnym repo

### Wrzucanie zmian

Aby wrzucić zmiany na zdalne repo:
```bash
git push origin <nazwa brancha>
```

Warto ustawić sobie upstream do brancha:
```bash
git push -u origin <nazwa brancha>

git push # nie potrzebna nazwa repo i brancha przy kolejnych pushach
```

> ### Uwaga
>
> Tylko zakommitowane zmiany można wypchnąć

### Zadanie

1. Utwórz w Githubie repo.
2. Wrzuć projekt nad którym wcześniej pracowaliśmy na Githuba.
3. Zmień coś w projekcie i wypchnij zmiany.

### Gałęzie śledzące zdalne zmiany

Każdy zdalny branch ma swój odpowiednik lokalnie.

Możemy je wyświetlić za pomocą `git branch -a`

Za pomocą `git fetch` możemy:
- pobrać nowego branche
- uaktualnić lokalne odpowiedniki branchy

### Pobieranie zmian

Jeśli w zdalnym repo pojawią się zmiany, to możemy chcieć je pobrać.

```bash
git pull origin <nazwa brancha>

git pull # jeśli mamy upstream analogicznie do `git push`
```

### Zadanie

1. Zedytuj plik w Githubie.
2. Zacommituj zmiany.
3. Pobierz te zmiany.

