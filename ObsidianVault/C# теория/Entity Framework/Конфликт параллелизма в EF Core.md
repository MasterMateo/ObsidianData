#EF 

EF Core реализует _оптимистическую параллельность_, которая предполагает, что конфликты параллелизма относительно редки.

В EF Core оптимистическое параллелизм реализуется путем _настройки свойства в качестве маркера_ параллелизма. Маркер параллелизма загружается и отслеживается при запросе сущности так же, как и любое другое свойство.

Свойство можно настроить:
- На стороне БД
	```C#
	public class Person
	{
    public int PersonId { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }

    [Timestamp]
    public byte[] Version { get; set; }
	}
	```
	(можно делать через FluentAPI)
	EF генерирует такой запрос:
	```SQL
	UPDATE [People] SET [FirstName] = @p0
	WHERE [PersonId] = @p1 AND [Version] = @p2;
	```
	Этот запрос исполнится, если `Version` столбец не изменился с момента запроса.
	 Если `Version` поменялся вылетит исключение `DbUpdateConcurrencyException`(оно должно обрататываться приложением)
- На стороне приложения
	```C#
	public class Person
	{
    public int PersonId { get; set; }
    public string FirstName { get; set; }

    [ConcurrencyCheck]
    public Guid Version { get; set; }
	}
	```
	(можно делать через FluentAPI)
	
	Так как это свойство не создается базой данных, его необходимо назначить в приложении при сохранении изменений:
	```C#
	var person = context.People.Single(b => b.FirstName ==       "John");
	person.FirstName = "Paul";
	person.Version = Guid.NewGuid();
	context.SaveChanges();
	```