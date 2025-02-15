## Лабораторная работа №1 15.02.2025
### Задание №1
![](/LabW1/1.png)
```
SELECT * FROM orders;
```
### Задание №2
![](/LabW1/2.png)
```
SELECT * FROM orders WHERE status IN ('cancelled','in_progress','delivery')
```
### Задание №3
![](/LabW1/3.png)
```
SELECT * FROM orders WHERE status = 'new' OR status = 'cancelled'
```
### Задание №4
![](/LabW1/4.png)
```
SELECT id,sum FROM orders WHERE products_count > 3
```
