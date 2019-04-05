# Задача 1. Посадочные места

## Описание

Для театра нужно сделать генератор посадочных мест на постановку. В зависимости от постановки количество рядов и кресел в ряду может меняться. При этом есть ограничение по количеству кресел

Также необходимо иметь возможность зарезервировать место при продаже билета

## Техническое задание

Необходимо написать две функции - для генерации карты посадочных мест и для резервирования места.

### Генерация карты посадочных мест

Функции генерации карты посадочных мест принимает количество рядов и мест в ряду, а так же количество доступных кресел.

На выходе функция должна вернуть двумерный массив, в котором все значения будут иметь значение `FALSE` (значение по умолчанию) - место не занято

Если количество посадочных мест на карте больше чем количество доступных кресел, то функция должна вернуть `FALSE`

### Резервирование места

Функция резервирования места должна принимать карту посадочных мест, номер ряда и номер места в ряду, которое нужно зарезервировать.

Если место свободно, то функция должна вернуть `TRUE` и на карте посадочных мест значение на соответствующей позиции должно измениться на `TRUE` - место занято

Если место уже занято, то функци должна вернуть `FALSE` и никак не менять значение на карте посадочных мест

Если ряд или место в ряду не существует, то функция должна вернуть `FALSE` и никак не менять значение на карте посадочных мест

\* *при реализации функции необходимо учитывать, что индекс массива начинается с 0, а нумерация рядов и мест с 1*

## Алгоритм выполнения

1. Создать файл `index.php`
2. Создать фукнцию `generate($rows, $placesPerRow, $avaliableCount)`
3. Создать функцию `reserve($map, $row, $place)`

Для проверки использовать следующий код:

```php
$chairs = 50;
$map = generate(5, 8, $chairs);
$requireRow = 3;
$requirePlace = 5;

$reverve = reserve($map, $requireRow, $requiredPlace);
logReserve($requireRow, $requirePlace, $reverve);

$reverve = reserve($map, $requireRow, $requiredPlace);
logReserve($requireRow, $requirePlace, $reverve);


function logReserve($row, $place, $result){
    if ($result) {
        echo "Ваше место забронировано! Ряд $row, место $place".PHP_EOL;
    } else {
        echo "Что-то пошло не так=( Бронь не удалась".PHP_EOL;
    }
}
```

После выполнения в консоли должен быть следующий вывод:
```
Ваше место забронировано! Ряд 3, место 5
Что-то пошло не так=( Бронь не удалась
```