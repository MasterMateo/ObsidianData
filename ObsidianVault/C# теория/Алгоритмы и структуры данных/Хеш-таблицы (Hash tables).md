#СтруктурыДанных 

Хеш-функция преобразует данные любой длины в данные фиксированной длины
![[Pasted image 20230802144040.png]]

Хеш-функция гарантирует генерацию тех же выходных значений для одних и тех же входных данных (например, передавая в функцию "abc" всегда будете получать "2"). Результат хэширования в криптографии невозможно инвертировать.
![[Pasted image 20230802144429.png]]

Мы не можем вставлять два значения по одному и тому же индексу(одинаковые значения хэша для разных ключей - collision)
![[Pasted image 20230802144649.png]]

Строя структуру данных основанную на хэшах нужно прийти к решению, которое решит 2 проблемы:
1. найти алгоритм хеширования, генерирующий различные индексы для различных ключей так, что коллизии возникают очень редко
2. найти алгоритм, разрешающий коллизии, которые в любом случае будут возникать

# Хеширование в примитивных типах и GetHashCode (BCL)

Хеш-функции сильно зависят от типа ключа:
1. целые числа (int etc.)
2. числа с плавающей точкой (float, double)
3. строки (string)
4. пользовательские структуры
5. пользовательские классы

## Советы по использованию GetHashCode:
1. GetHashCode следует использовать только для добавление объекта в хеш-таблицу
2. идентичные элементы должны иметь идентичные хеши
3. Результат GetHashCode для элемента не должен меняться пока элемент хранится в структуре данных, работоспосоность которой зависит от стабильного хеша
4. GetHashCode не должен выбрасывать исключения

## Хорошая реализация хеширования должна:
1. быть быстрой!
2. хорошо распределенной в пространстве 32-битных целых чисел для заданного распределения входных значений
## Не используйте хеш-коды:
1. как уникальный ключ объекта: верятность коллизий слишком высока
2. как часть цифровой подписи или как эквивалент пароля

Вычисление хеш-кода ссылочных типов данных не использует внутренее состояние объекта, в отличии от вычисления хеш-кода типовых значений!