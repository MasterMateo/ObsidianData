#CSharp 

Класс Interlocked предоставляет методы, позволяющие выполнять инкремент, декремент, обмен и считывание значений потокобезопасно

- **CompareExchange()** - Безопасно проверяет два значения на эквивалентность. Если они эквивалентны, изменяет первое из значений на третье
	```C#
	InterLocked.CompareExchange(Int32, Int32, Int32);
	```
	 *может быть любым типом(даже Object)	
- **Decrement()** - Безопасно уменьшает значение на 1
	```C#
	Interlocked.Decrement(ref count)
	```
- **Increment()** - Безопасно увеличивает значение на 1
	```C#
	int count = 0;
	collection.AsParallel()
	.ForAll(p =>
	{
		if (p.Contains('s'))
			Interlocked.Increment(ref count)
	})
	```
- **Exchange()** - Безопасно меняет два значения местами
	```C#
	Interlocked.Exchange(ref myInt, 83);
	```