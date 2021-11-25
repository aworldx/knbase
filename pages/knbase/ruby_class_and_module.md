---
title: Модуль и класс в Ruby
keywords: ruby
summary: "This is just a sample topic..."
sidebar: knbase_sidebar
permalink: ruby_class_and_module.html
folder: knbase
---

## Модуль и класс в Ruby
- модуль не может быть инстанциирован
- класс может наследоваться только от одного класса
- но в класс можно включить несколько модулей
- модуль не поддерживает наследование
- superclass класса - Module
- superclass модуля - Object
- модули включаются в класс в обратном порядке (приоритет у нижнего)
- методы класса имеют приоритет над одноименными методами модуля
- prepend делает метод модуля более приоритетным по сравнению с одноименным методом класса