#SQL

- __INNER JOIN__ - это соединение двух таблиц, при котором каждая запись из первой таблицы соединяется с каждой записью второй таблицы, создавая тем самым все возможные комбинации записей обеих таблиц (декартово произведение)
- __OUTER JOIN__ - внешнее соединение. Главным отличием внешнего соединения от внутреннего является то, что оно обязательно возвращает все строки одной (LEFT, RIGHT) или двух таблиц (FULL)
	- Внешнее левое соединение (LEFT OUTER JOIN)
		Соединение, которое возвращает все значения из левой таблицы, соединённые с соответствующими значениями из правой таблицы если они удовлетворяют условию соединения, или заменяет их на NULL в обратном случае.
	- Внешнее правое соединение (RIGHT OUTER JOIN)
		Соединение, которое возвращает все значения из правой таблицы, соединённые с соответствующими значениями из левой таблицы если они удовлетворяют условию соединения, или заменяет их на NULL в обратном случае
	- Внешнее полное соединение (FULL OUTER JOIN)
		Соединение, которое выполняет внутреннее соединение записей и дополняет их левым внешним соединением и правым внешним соединением.
	Алгоритм работы полного соединения:
	1. Формируется таблица на основе внутреннего соединения (INNER JOIN).
	2. В таблицу добавляются значения не вошедшие в результат формирования из левой таблицы (LEFT OUTER JOIN). 
	3. В таблицу добавляются значения не вошедшие в результат формирования из правой таблицы (RIGHT OUTER JOIN).
- __CROSS JOIN__ - перекрестное (или декартово) произведение. Каждая строка одной таблицы соединяется с каждой строкой второй таблицы, давая тем самым в результате все возможные сочетания строк двух таблиц. 

