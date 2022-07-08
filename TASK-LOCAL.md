# Zadanie - książka

Piszemy książkę o HTML w markdown (plik z rozszerzeniem `.md`)

> Podstawy o składni markdown
>
> https://www.markdownguide.org/basic-syntax/
>
> Tak naprawdę potrzebujemy tylko nagłówki oraz akapity.

## Zadanie 1 

1. Utwórz repozytorium i dodaj do niego pusty plik markdown.
2. Następnie wykorzystaj poniższą dokumentację, żeby napisać wstęp książki oraz 2 krótkie rozdziały (możesz dosłownie przekleić treść).
https://developer.mozilla.org/pl/docs/Learn/HTML
3. Treści najwygodniej będzie Ci dodać przez VSC.
> Pamiętaj, żeby te zmiany dodać do repo!

## Zadanie 2

1. Na nowym branchu utwórz kolejny rozdział.
> Dobrze jest pamiętać o odpowiednim nazewnictwie branchy `feature/<jakiś opis>`
2. Domerguj ten rozdział do `main`.
3. Następnie usuń ten branch. 

## Zadanie 3

1. Na nowym branchu nanieć poprawki do pierwszego rozdziału i wstępu.
2. Chcemy wysłać te poprawki do redakcji. Sprawdź jakie zmiany zostały dokonane na tym branchu.

## Zadanie 4

1. Na nowym branchu usuń pierwszy rozdział.
2. Domerguj ten branch do `main`.
3. Następnie domerguj do `main` branch z zadania 3.
4. Rozwiąż konflikty w VSC.
5. Usuń oba branche.

## Rozwiązania zadań 
|

|

|

|

|

|

|

|

|

|

|

|

|

|

|

|

### Zadanie 1
``` bash
mkdir book
cd book
git init
touch BOOK.md

# dodanie treści

git add BOOK.md
git commit -m "create book"
```

### Zadanie 2
``` bash
git checkout -b feature/new-chapter

# dodanie treści

git add BOOK.md
git commit -m "add chapter"

git checkout main
git merge feature/new_chapter
git branch -d feature/new_chapter
```

### Zadanie 3
``` bash
git checkout -b feature/changes

# zmiana treści

git add BOOK.md
git commit -m "change intro and first chapter"

git diff main
```


### Zadanie 3
``` bash
git checkout -b feature/delete-chapter

# usunięcie rozdziału

git add BOOK.md
git commit -m "delete first chapter"

git checkout main
git merge feature/changes
git merge feature/delete-chapter

# rozwiąż konflikty

git branch -d feature/delete-chapter
git branch -d feature/changes
```