#CSharp 

LINQ (Language-Integrated Query) представляет простой и удобный язык запросов к источнику данных. В качестве источника данных может выступать объект, реализующий интерфейс IEnumerable (например, стандартные коллекции, массивы), набор данных DataSet, документ XML. Но вне зависимости от типа источника LINQ позволяет применить ко всем один и тот же подход для выборки данных.

В LINQ можно выделить 2 типа методов:
1. Отложенные(Deferred)
	1. При их использовании происходит конструирование запроса(т.е. он не исполняется сразу) - Select, SelectMany, Take, Skip, Where и др.
2. Жадные(Greedy)
	1. В таком случае выполнение запроса происходит в двух случаях, первое когда по результатам запроса мы запускаем `foreach`, второе когда на результатах запроса вызываем greedy оператор - Min, Count, Max, ToList, ToArray, Average, Sum и др.

Если мы будем модифицировать коллекцию, до того как будет вызван greedy оператор, мы можем получить то, чего не ожидаем:
```C#
var list = new List<int> {1,2,3};
var query = list.Where(c => c >= 2);
list.Remove(3);
query.Count() // = 1!
```

`Count()` передаст значение 1, так как метод `Where` будет вызван перед выполнением `Count()`(отложенный оператор), так как коллекция была модифицирована, то цифры 3 в ней на момент вызова `Where` уже нет.
Если мы хотим выполнить `Where` сразу нужно добавить в конце greedy оператор, например:
```C#
var list = new List<int> {1,2,3};
var query = list.Where(c => c >= 2).ToList();
list.Remove(3);
query.Count() // = 2
```


![[Pasted image 20231224173210.png]]

Существует несколько разновидностей LINQ:

- __*LINQ to Objects*__: применяется для работы с массивами и коллекциями 
- __*LINQ to Entities*__: используется при обращении к базам данных через технологию Entity Framework    
- __*LINQ to XML*__: применяется при работе с файлами XML    
- __*LINQ to DataSet*__: применяется при работе с объектом DataSet    
- __*Parallel LINQ (PLINQ)*__: используется для выполнения параллельных запросов

## Часто используемые методы:

- __Select__: определяет проекцию выбранных значений    
- __Where__: определяет фильтр выборки    
- __OrderBy__: упорядочивает элементы по возрастанию    
- __OrderByDescending__: упорядочивает элементы по убыванию    
- __ThenBy__: задает дополнительные критерии для упорядочивания элементов возрастанию    
- __ThenByDescending__: задает дополнительные критерии для упорядочивания элементов по убыванию    
- __Join__: соединяет две коллекции по определенному признаку    
- __Aggregate__: применяет к элементам последовательности агрегатную функцию, которая сводит их к одному объекту    
- __GroupBy__: группирует элементы по ключу    
- __ToLookup__: группирует элементы по ключу, при этом все элементы добавляются в словарь    
- __GroupJoin__: выполняет одновременно соединение коллекций и группировку элементов по ключу    
- __Reverse__: располагает элементы в обратном порядке    
- __All__: определяет, все ли элементы коллекции удовлятворяют определенному условию    
- __Any__: определяет, удовлетворяет хотя бы один элемент коллекции определенному условию    
- __Contains__: определяет, содержит ли коллекция определенный элемент
- __Distinct__: удаляет дублирующиеся элементы из коллекции    
- __Except__: возвращает разность двух коллекцию, то есть те элементы, которые создаются только в одной коллекции    
- __Union__: объединяет две однородные коллекции    
- __Intersect__: возвращает пересечение двух коллекций, то есть те элементы, которые встречаются в обоих коллекциях    
- __Count__: подсчитывает количество элементов коллекции, которые удовлетворяют определенному условию    
- __Sum__: подсчитывает сумму числовых значений в коллекции    
- __Average__: подсчитывает cреднее значение числовых значений в коллекции    
- __Min__: находит минимальное значение    
- __Max__: находит максимальное значение    
- __Take__: выбирает определенное количество элементов    
- __Skip__: пропускает определенное количество элементов    
- __TakeWhile__: возвращает цепочку элементов последовательности, до тех пор, пока условие истинно    
- __SkipWhile__: пропускает элементы в последовательности, пока они удовлетворяют заданному условию, и затем возвращает оставшиеся элементы    
- __Concat__: объединяет две коллекции    
- __Zip__: объединяет две коллекции в соответствии с определенным условием    
- __First__: выбирает первый элемент коллекции    
- __FirstOrDefault__: выбирает первый элемент коллекции или возвращает значение по умолчанию    
- __Single__: выбирает единственный элемент коллекции, если коллекция содержит больше или меньше одного элемента, то генерируется исключение    
- __SingleOrDefault__: выбирает единственный элемент коллекции. Если коллекция пуста, возвращает значение по умолчанию. Если в коллекции больше одного элемента, генерирует исключение    
- __ElementAt__: выбирает элемент последовательности по определенному индексу    
- __ElementAtOrDefault__: выбирает элемент коллекции по определенному индексу или возвращает значение по умолчанию, если индекс вне допустимого диапазона    
- __Last__: выбирает последний элемент коллекции    
- __LastOrDefault__: выбирает последний элемент коллекции или возвращает значение по умолчанию


![[Pasted image 20240209164045.png]]

![[Pasted image 20240209164330.png]]