#GRASP 

- Проблема
	- Как обрабатывать альтернативные варианты поведения на основе типа?
	- Как подключить систему основанную на подключаемых модулях?
- Решение
	-  Обязанности распределяются для различных вариантов поведения с помощью полиморфных операций для этого класса
	- Каждая внешняя система имеет свой интерфейс

[[Polymorphism.excalidraw]]

- Преимущества
	- Впоследствии легко расширять и модернизировать систему
- Недостатки
	- Не следует злоупотреблять добавлением интерфейсов с применением принципа полиморфизма с целью обеспечения дееспособности системы в неизвестных заранее новых ситуациях (KISS)