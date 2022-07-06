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


