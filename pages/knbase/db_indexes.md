---
title: Indexes
keywords: db
summary: "This is just a sample topic..."
sidebar: knbase_sidebar
permalink: db_indexes.html
folder: knbase
---

## Виды индексов в postgres

Postgres поддерживает 5 типов индексов:
- B-дерево,
- хеш
- GiST
- SP-GiST
- GIN
- BRIN

### Особенности B-дерева
- индекс по умолчанию в Rails
- самый популярный
- работает только с сортируемыми данными: < <= = >= >

### Особенности хеш индекса
- работает только с простыми условиями равенства
- не рекомендуется их использовать

## Сотавные индексы

...

## Индексы и сортировка

...


### Ссылки
- https://postgrespro.ru/docs/postgresql/9.6/indexes-types
- https://tproger.ru/articles/indeksy-v-postgresql/