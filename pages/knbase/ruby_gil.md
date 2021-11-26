---
title: Global Interpreter Lock
keywords: ruby
summary: "This is just a sample topic..."
sidebar: knbase_sidebar
permalink: ruby_gil.html
folder: knbase
---

- ограничивает параллелизм
- делает код потокобезопасным
- в многопоточном окружении в некоторый момент времени может выполняться Ruby-код только в одном потоке
- GIL есть только в MRI, его нет в JRuby или Rubinius (это интерпретаторы)

```
В MRI есть нечто, называемое GIL (global interpreter lock, глобальная блокировка интерпретатора). Благодаря ей в многопоточном окружении в некоторый момент времени может выполняться Ruby-код только в одном потоке.

Например, если у вас есть восемь потоков, работающих на восьмиядерном процессоре, только один поток может работать в некоторый момент времени. GIL призвана предотвратить появление гонки условий, которая может нарушить целостность данных. Есть некоторые тонкости, но суть такова.
```

### Пример потоконебезопасного кода
```
array = []

5.times.map do
  Thread.new do
    1000.times do
      array << nil
    end
  end
end.each(&:join)

puts array.size
```

```
$ ruby pushing_nil.rb
5000

$ jruby pushing_nil.rb
4446

$ rbx pushing_nil.rb
3088
```

### Как сделать код потокобезопасным ?
- использовать mutex. Делает операции атомарными. ОС может переключить контекст на другой поток, но новый поток не будет иметь доступа к мьютексу.
```
array = []
mutex = Mutex.new

5.times.map do
  Thread.new do

    mutex.synchronize do
      1000.times do
        array << nil
      end
    end

  end
end.each(&:join)

puts array.size
```

## Ссылки
- https://habr.com/ru/post/189320/