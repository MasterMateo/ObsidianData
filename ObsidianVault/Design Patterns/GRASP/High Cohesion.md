#GRASP 

- Проблема
	- Необходимо сделать наименьшее кол-во взаимосвязей между объектами в системе
- Решение
	- Сделать так, чтобы каждый класс отвечал только за одну функцию. Каждый класс должен быть внутри "зацеплен"(логически связан). Максимизировать связность внутри каждой единицы
- Преимущество
	- Классы с высокой степень зацепления просты в поддержке и повторонм использовании
- Недостатки
	- Иногда бывает неоправданно использовать высокое зацепление для распределения серверных объектов. В этом случае лучше создать несколько более крупных серверных объектов со слабым зацеплением