#СтруктурыДанных 
FIFO - first-In, first-Out
1. Enqueue - добавление эелемента в очередь
2. Dequeue - удаление элемента
3. Peek - взятие элемента из начала очереди без удаления

# Тип Queue в BCL

Из документации: "Фактор роста - число на котрое умножается текущая емкость при необходимости расширения. Определяется в момент конструирования очереди. По умолчанию =2. Емкость очереди расширяется минимум на 4 элемента независимо от фактора роста. Например, если фактор роста = 1, то очередь всегда будет расширяться на 4 элемента". Клиент не может управлять фактором роста, подлежащий массив всегда будет расти в 2 раза.
Дефолтный размер массива очереди 4, но в конструкторе можно указать нужное значение

Характеристкики:
1. Основана на массиве (кольцевая)
2. `Peek/Dequeue` - константное время
3. `Enqueue` - линейное время если требует пересоздание массива, за константу если не требуется
4. `Contains` - работает за линейное время - проход по N узлам
5. `CopyTo/ToArray` - линейное время, так как надо копировать N элементов
6. `Clear` - линейное время, так как внутри вызывается `Array.Clear`, который присваивает `default(T)` каждому элементу очереди
7. `TrimToSize` - линейное время, потому что нам необходимо сузить массив


## Характеристики в общем:

1. Peek работает за константное время в любом случае
2. Если очередь базируется на связном списке:
	1. Enqueue/Dequeue - за константное время
3. Если очередь базируется на массиве:
	1. если достаточно места Enqueue - константное время
	2. если недостаточно места, Enqueue - за линейное время(из-за изменения размера массива)
	3. Dequeue работает за константу если не сужаем массив, если сужаем то линейное время(это редко, в основном массив не сужается)
4. Если на устройстве достаточно памяти или макс кол-во элементов неизвестно -> связный список можно предпочесть массиву в качестве основы для очереди
5. Если памяти недостаточно или маск кол-во элементов известно заранее -> массив можно предпочесть связному списку

