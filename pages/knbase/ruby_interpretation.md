---
title: Интерпретация руби программ
keywords: ruby
summary: "This is just a sample topic..."
sidebar: knbase_sidebar
permalink: ruby_interpretation.html
folder: knbase
---

## Интерпретация руби программ
- чтение файла
- токенизация
- парсинг, построение AST дерева (abstract syntax tree)
- Ruby <= 1.8 выполняет интрукции из AST дерева. Ruby >= 1.9 компилирует код для виртуальной машины YARV
- подготовка инструкции для VM (компиляция)
- выполнение инструкции виртуальной машины