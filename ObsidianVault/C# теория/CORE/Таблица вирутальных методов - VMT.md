#CSharp 

Для работы с виртуальными методами компилятор формирует таблицу виртуальных методов (Virtual Method Table или VMT). В нее записывается адреса виртуальных методов. Для каждого класса создается своя таблица.

Когда создается объект класса, то компилятор передает в конструктор объекта специальный код, который связывает объект и таблицу VMT.

А при вызове виртуального метода из объекта берется адрес его таблицы VMT. Затем из VMT извлекается адрес метода и ему передается управление. То есть процесс выбора реализации метода производится во время выполнения программы. Собственно так и выполняется виртуальный метод. Следует учитывать, что так как среде выполнения вначале необходимо получить из таблицы VMT адрес нужного метода, то это немного замедляет выполнение программы.

Есть два способа изменения функциональности методов, унаследованных от базового класса:
1. __Переопределение__(virtual -> override)
```C#
Person tom = new Employee("Tom","Microsoft");
tom.Print(); //вызовет реализзацию класса Employee 
```
2. __Cкрытие__(определяем метод в классе-наследнике с модицикатором `new`)
```C#
Person tom = new Employee("Tom","Microsoft");
tom.Print(); //вызовет реализзацию класса Person 
```

Класс Employee никак не переопределяет метод Print, унаследованный от базового класса, а фактически определяет новый метод. Поэтому при вызове `tom.Print()` вызывается метод Print из класса Person.