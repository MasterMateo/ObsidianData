#CSharp 

enum, который позволяет просмаривать состояние жизненого цикла задачи

- `Created` - создана
- `WaitingForActivation` - ожидает внутреннего планирования платформой .net
- `WaitingToRun` - ожидает запуска
- `Running` - выполняется
- `WaitingForChildrenToComplete` - ожидает завершения дочерних задач
- `Canceled` - задача отменена(бросает спец искл)
- `RanToCompletion` - выполнена
- `Faulted` - задача заввершилась из-за исключения