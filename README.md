# dzheni_genetic_algorithm
first lab for dzheni

modify only config.cfg

Запуск скрипта: 
### python3 main.py

## Постановка задачи
Дано: I = {1 , ... , n} - множество городов, матрица C[i,j] - попарные 
расстояния между городами 1<=i, j<=n. x[i,j] = 1, если из города i едем в 
город j, в противном случае x[i,j] = 0.  
Найти: контур минимальной длины (цикл), проходящий через каждую 
вершину ровно 1 раз и имеющий минимальный вес. 
min ( ∑i ∑j c[i,j] * x[i,j] ). При этом в одном столбце и в одной 
строке может быть только 1 единица и ∑i⊂S∑i⊂I/S x[i,j]>=1, ∀S⊂I, S!= ∅

## Формализация допустимого решения
Вектор X длины n, где xi - город,
который посещается на i-ом моменте времени

## Алгоритм генерации допустимого решения (популяции)
Генерируем m векторов длины n следующими образом: 
1 шаг: выбираем случайным образом число от 1 до n 
2 шаг: исключаем выбранное число из выборки 
3 шаг: повторяем шаги 1-2, пока не получим вектор из n чисел
 
## Кроссовер (алгоритм)
Случайным образом выбираем точку разрыва
Формируем потомков: 
1 потомок:
маршрут второго родителя до точки разрыва, оставшиеся города идут в порядке, в котором расположены в первом родителе
2 потомок:
маршрут первого родителя до точки разрыва, оставшиеся города идут в порядке, в котором расположены во втором родителе

## Мутация
Оператор инверсии (случайным образом выбирается точка разрыва от 1 до n-1, вектор делится на 2 части, части меняются местами)

## Выбор родителей
Пропорциональный отбор:
выбираем родителей с вероятностями, 
обратно пропорциональными функции принадлежности

## Отбор особей в новую популяцию
Пропорциональный отбор:
выбираем m особей с вероятностями, 
обратно пропорциональными функции принадлежности

## Критерий остановки
1. l эпох
2. стабилизация функции приспособленности с точностью z

## Входные параметры и исходные данные алгоритма
Смотреть config.cfg
"m" : 100,
"n" : 10,
"k" : 10,
"l" : 300,
"z" : 0.01,
"pc" : 0.7,
"pm" : 0.3,
"min_dist" : 2,
"max_dist" : 100
