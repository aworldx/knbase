---
title: Preloading
keywords: rails
summary: "This is just a sample topic..."
sidebar: knbase_sidebar
permalink: rails_preloading.html
folder: knbase
---

## Preload
- загружает ассоциации в отдельном запросе
- условия по ассоциации писать нельзя

## Includes
- сама выбирает загружать ассоциацию одним запросом или несколькими
- можно писать условия для ассоциации
- соединение использует LEFT JOIN

## Eager load
- всегда загружает ассоциации одним запросом используя LEFT JOIN

## Joins
- INNER JOIN
- до версии Rails 5 чтобы сделать LEFT JOIN надо было писать
```
Catalog.joins('LEFT JOIN items ON catalogs.id = items.catalog_id')
```
- после версии 5 включительно появился метод left_joins
```
Catalog.left_joins(:items)
```