#GOF 

Проблема:
	 - Определить интерфейс для создания объекта, но оставить подклассам решение о том, какой класс инстанциировать, то есть, делегировать инстанциирование подклассам
Используется, когда:
	- бизнес-объект меняется в runtime
	- бизнес-объекты могут меняться
	- повторное использование наработанного функционала

[[FactoryMethod.excalidraw]]

Преимущества:
	- Избавляет проектировщика от необходимости встраивать в код зависящие от приложения классы
Недостатки:
	 - Возникает доп уровень под классов
