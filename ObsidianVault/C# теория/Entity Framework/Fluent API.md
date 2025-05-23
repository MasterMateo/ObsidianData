#EF 

Модель в Entity Framework представляет набор всех сущностей и связей между ними, которыми управляет контекст данных. Все сущности, с которыми работает Entity Framework Core и которые хранятся в базе данных, определяются в C# в виде классов. При этом Entity Framework применяет ряд условностей для сопоставления классов с таблицами. Например, названия столбцов должны соответствовать названиям свойств и т.д. В этом случае Entity Framework сможет сопоставить столбцы таблицы и свойства классов.

Однако с помощью таких механизмов, как Fluent API и аннотации данных мы можем добавить дополнительные правила конфигурации, либо переопределить используемые условности.

Fluent API представляет набор методов, которые определяют сопоставление между классами и их свойствами и таблицами и их столбцами. Для использования функционала Fluent API переопределяется метод OnModelCreating()

![[Pasted image 20231014132805.png]]
![[Pasted image 20231014134743.png]]
![[Pasted image 20231014134805.png]]

## Relationships in Fluent API

One to One
![[Pasted image 20231014135528.png]]

Чтобы сделать
![[Pasted image 20231014135839.png]]

One to Many
![[Pasted image 20231014194056.png]]

Чтобы сделать
![[Pasted image 20231015104312.png]]

Many to Many
![[Pasted image 20231015105038.png]]

Чтобы сделать
![[Pasted image 20231015105236.png]]