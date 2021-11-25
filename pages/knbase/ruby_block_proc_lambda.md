---
title: Block proc lambda
keywords: ruby
summary: "This is just a sample topic..."
sidebar: knbase_sidebar
permalink: ruby_block_proc_lambda.html
folder: knbase
---

## Block Proc Lambda
- блоки, проки, лямбды - это замыкания
- блоки используются чтобы передать кусок кода в метод
- проки и лямбды позволяют сохранить блоки в переменных
- блок может передаваться явно и неявно

```
def met(&block)
    block.call
end    
```

- когда блок передается явно в переменную, он автоматически конвертируется в proc
- proc is instance of Proc class

```
proc = Proc.new { |n| ... }
```

- так как proc может сохраняться в переменной, он может быть передан в метод как обычный аргумент, и не нужно использовать &

```
def met(proc)
    proc.call()
end
```

Пример:

```
[1,2,3].map(&:to_s)
```

здесь & это конвертация в proc (вызов to_proc метода у :to_s (класса Symbol))

```
class Symbol
    def to_proc
        Proc.new { |i| i.send(self) }
    end
end        
```

- лямбды это те же проки с некоторыми отличиями
  - требует чтобы все аргументы были переданы
  - return внутри proc совершит выход из метода, в котором proc был вызван
  - return внутри lambda совершит выход только из блока описывающего лямбду  