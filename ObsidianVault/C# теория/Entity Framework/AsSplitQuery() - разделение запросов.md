#EF 

Добавлен в 5 версии, данный метод разделяет запрос(заставит query provider транслировать загрузку связанной коллекции отдельным запросом)

Если запрос использует `Include` для возврата нескольких связанных коллекций, это может привести к снижению производительности

`AsSplitQuery()` позволяет разделять один LINQ-запрос, включая связанные коллекции, на несколько SQL-запросов

Например, мы выгружаем из бд пост, который набрал 1000 комментариев. Делая `Join` (`Include`) мы будем 1000 раз выгружать нужный пост чтобы достать все комментарии, что может тормозить бд. Используя `AsSplitQuery()` мы выгрузим пост 1 раз. Для нескольких коллекций поведение будет аналогичное, что избавит от комбинаторного взрыва.

Пример:
```C#
var artists = context.Artists
    .Include(e => e.Albums)
    .ToList();
```
Такой запрос по умолчанию создаст:
```SQL
SELECT a.Id, a.Name, al.Id, al.ArtistId, al.Title
FROM Artists AS a
LEFT JOIN Album AS al ON a.Id = al.ArtistId
ORDER BY a.Id, a0.Id
```
Используем AsSplitQuery():
```C#
var artists = context.Artists
    .Include(e => e.Albums)
    .AsSplitQuery()
    .ToList();
```
Тогда будет:
```SQL
SELECT a.Id, a.Name
FROM Artists AS a
ORDER BY a.Id

SELECT al.Id, a0.ArtistId, a0.Title, a.Id
FROM Artists AS a
INNER JOIN Album AS a0 ON a.Id = a0.ArtistId
ORDER BY a.Id
```