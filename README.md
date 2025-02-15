## Лабораторная работа №1 15.02.2025
### Задание №1
Выберите из таблицы orders все заказы

![](/LabW1/1.png)
```
SELECT * FROM orders;
```
### Задание №2
Выберите из таблицы orders все заказы кроме новых. У новых заказов status равен "new". Использовать in

![](/LabW1/2.png)
```
SELECT * FROM orders WHERE status IN ('cancelled','in_progress','delivery')
```
### Задание №3
Выберите из таблицы orders все новые и отмененные заказы. У отмененных заказов status равен "cancelled". У новых заказов status равен "new"

![](/LabW1/3.png)
```
SELECT * FROM orders WHERE status = 'new' OR status = 'cancelled'
```
### Задание №4
Выберите из таблицы orders все заказы содержащие более 3 товаров (products_count).
Вывести нужно только номер (id) и сумму (sum) заказа

![](/LabW1/4.png)
```
SELECT id,sum FROM orders WHERE products_count > 3
```
