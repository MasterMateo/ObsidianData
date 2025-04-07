#CSharp 

_Фабрика задач_ - механизм, позволяющий настроить набор сгруппированных задач, которые находятся в одном состоянии

Классы для работы с фабрикой `TaskFactory` и `TaskFactory<TResult>`

```C#
TaskFactoty taskFactory = new TaskFactory();

Task<double> t1 = taskFactory.StartNew(() => {return Calc(1); });
Task<double> t2 = taskFactory.StartNew(() => {return Calc(2); });
Task<double> t3 = taskFactory.StartNew(() => {return Calc(3); });

taskFactory.ContinueWhenAll(new Task[] {t1, t2, t3},
						   tasks =>
						   {
							   duble sum = 0;
							   foreach(var item in tasks)
							   {
								   sum+= item.Result;
							   }
							Console.Writeline($"Sum:{sum}")
						   });
```

`ContinueWhenAll` - продолжение будет выполняться после завершения всех задач