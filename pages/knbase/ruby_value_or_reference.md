---
title: Pass by reference o value
keywords: ruby
summary: "This is just a sample topic..."
sidebar: knbase_sidebar
permalink: ruby_value_or_reference.html
folder: knbase
---

```ruby
def foo(bar)
    bar = 'reference'
end
 
baz = 'value'
foo(baz)
puts "Ruby is pass-by-#{baz}"


=> Ruby is pass-by-value
```

И так руби передает параметры по значению.  
НО! Переменные в руби это всегда ссылки.  
Таким образом при передаче ссылки по значению, ссылка копируется.  
Скопированная ссылка указывает на ту же область памяти.  
Объект по этому адресу можно изменить, если у него есть мутирующие методы.  
Присваиванием же мы не меняем объект, а создаем новую ссылку на этот объект.
Новая ссылка (после присваивания) никак не затронет ссылку которая пришла через входной параметр, потому что она была передана by value.

### RUBY immutable objects
- numbers
- booleans
- nil
- range
- true , false
