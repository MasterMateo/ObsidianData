#CSharp 

Продолжения - это асинхронная задача, вызываемая другой задачей при своем завершении

Для добавления продолжения используется метод `ContinueWith()`

```C#
Task task = new Tast(new Action(Download));
Task continuation = task.ContinueWith(new Action<Task>(ShowData))
```

`ContinueWith()` возвращается новый экземпляр класса Task, что позволяет выстраивать цепочки продолжений

Имеются `TaskContiniationOptions` - enum в котором находятся настройки продолжений(пр. запускать продолжение синхронно)