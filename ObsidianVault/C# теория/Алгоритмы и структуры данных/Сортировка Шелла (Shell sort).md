#Алгоритмы 
Улучшенная версия сортировки вставками (Insertion sort)
Базовая идея этой сортировки в том, чтобы предварительно отсортировать (специальным образом) элементы и переключиться на сортировку вставками. 
Для предварительно соритровки используется **gap** - позволяет обменять местами далеко отстоящие друг от друга элементы, по ходу выполнения алгоритма gap уменьшается, пока не станет равно 1. После этого мы переключаемся на сортировку вставками.

Применение "универсальной" последовательности для расчета **gap**:
1. Вычислить начальный максимальный gap (не должен быть больше или равен n/3)
2. Сокращать gap в конце каждой итерации внешнего цикла, деля его на 3

Характеристики:
1. "in-place" алгоритм (малое кол-во доп памяти)
2. Нестабильный (неустойчивый)
3. Временна сложность 1/2 * ($3^{k}$ - 1)
