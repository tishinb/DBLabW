## Лабораторная работа №1 [15.02.2025]

### Таблица

![](/LabW1/0_table.png)

### Задание №1

Выберите из таблицы orders все заказы

![](/LabW1/1.png)

``` sql
SELECT * FROM orders;
```

### Задание №2

Выберите из таблицы orders все заказы кроме новых. У новых заказов status равен "new". Использовать in

![](/LabW1/2.png)

``` sql
SELECT * FROM orders WHERE status IN ('cancelled','in_progress','delivery')
```

### Задание №3

Выберите из таблицы orders все новые и отмененные заказы. У отмененных заказов status равен "cancelled". У новых заказов status равен "new"

![](/LabW1/3.png)

``` sql
SELECT * FROM orders WHERE status = 'new' OR status = 'cancelled'
```

### Задание №4

Выберите из таблицы orders все заказы содержащие более 3 товаров (products_count).
Вывести нужно только номер (id) и сумму (sum) заказа

![](/LabW1/4.png)

``` sql
SELECT id,sum FROM orders WHERE products_count > 3
```

## Лабораторная работа №2 [22.02.2025]

### Задание №161

#### Таблица

![](/LabW2/161/0_table.png)

1) Выберите из таблицы orders 3 самых дешевых заказа за всё время.
Данные нужно отсортировать в порядке убывания цены.
Отмененные заказы не учитывайте.

![](/LabW2/161/1.png)

``` sql
select * from orders where status in('new','in_progress','delivery') order by sum desc limit 3;
```

2) Выберите из таблицы orders 2 самых дорогих заказов за всё время.
Данные нужно отсортировать в порядке убывания цены.
Отмененные заказы не учитывайте.

![](/LabW2/161/2.png)

``` sql
select * from orders where status in('new','in_progress','delivery') order by sum desc limit 2;
```

### Задание №166

#### Таблица

![](/LabW2/166/0_table.png)

3) Добавьте в таблицу orders данные о новом заказе стоимостью 8000 рублей. В заказе 4 товара (products).

![](/LabW2/166/1.png)

``` sql
insert into orders (id, products, sum) value (6, 4, 8000);
```

#### Результат:

![](/LabW2/166/1_result.png)

### Задание №167

#### Таблица

![](/LabW2/167/0_table.png)

4) Добавьте в таблицу products новый товар — «VR-очки», стоимостью 70000 рублей в количестве (count) 2 штук.
   
![](/LabW2/167/1.png)

``` sql
insert into products (id, name, count, price) value (7, 'VR-очки', 2, 70000);
```

#### Результат:

![](/LabW2/167/1_result.png)

### Задание №172

#### Таблица

![](/LabW2/172/0_table.png)

5) В таблицу products внесли данные с ошибкой, вместо "PS5" в наименовании написали IMAC. Исправьте ошибку.

![](/LabW2/172/1.png)

``` sql
update products set name='PS5' where id=7;
```

#### Результат:

![](/LabW2/172/1_result.png)

## Лабораторная работа №3 [01.03.2025]

Создайте таблицу users с полем id типа INT и двумя текстовыми полями, которые будут хранить имя (first_name) и фамилию (last_name). Длина имени и фамилии не превышает 50 символов.
Добавьте в таблицу трех пользователей: Дмитрия Иванова, Анатолия Белого и Дениса Давыдова.

![](/LabW3/1.png)

``` sql
CREATE TABLE users (
    id INT,
    first_name VARCHAR(50),
    last_name VARCHAR(50)
);
INSERT INTO users (id, first_name, last_name)
VALUES
    (1, 'Дмитрий', 'Иванов'),
    (2, 'Анатолий', 'Белый'),
    (3, 'Денис', 'Давыдов');
```

#### Результат:

![](/LabW3/2.png)

## Лабораторная работа №4 [15.03.2025]

### Задание №1

Создайте таблицу users для хранения информации о пользователях сайта.
В таблице должны быть следующие поля:

id – идентификатор, целое положительное;
email – адрес электронной почты, строка не более 100 символов;
date_joined – дата регистрации (достаточно хранить дату, без времени)
last_activity – дата и время последней активности (с точностью до секунд).

![](/LabW4/5379620308778087112.jpg)

#### Неверное решение:

``` sql
CREATE TABLE users(
id INT UNSIGNED,
email VARCHAR(100),
date_joined DATE,
last_activity DATETIME
);

INSERT INTO users (id, email, date_joined, last_activity)
VALUES (1, "user1@domain.com", "2014-12-12", "2016-04-08 12:34:54")
INSERT INTO users (id, email, date_joined, last_activity)
VALUES (2, "user2@domain.com", "2014-12-12", "2017-02-13 11:46:53")
INSERT INTO users (id, email, date_joined, last_activity)
VALUES (3, "user3@domain.com", "2014-12-13", "2017-04-04 05:12:07")
```
#### Правильное решение 1:

То же самое, но разделяется точкой с запятой

``` sql
CREATE TABLE users(
id INT UNSIGNED,
email VARCHAR(100),
date_joined DATE,
last_activity DATETIME
);

INSERT INTO users (id, email, date_joined, last_activity)
VALUES (1, "user1@domain.com", "2014-12-12", "2016-04-08 12:34:54");
INSERT INTO users (id, email, date_joined, last_activity)
VALUES (2, "user2@domain.com", "2014-12-12", "2017-02-13 11:46:53");
INSERT INTO users (id, email, date_joined, last_activity)
VALUES (3, "user3@domain.com", "2014-12-13", "2017-04-04 05:12:07");
```

#### Правильное решение 2 (Красивее):

``` sql
create table users (
id int(10) unsigned,
email varchar (100),
date_joined date,
last_activity datetime
);
insert into users (id, email, date_joined,last_activity)
values
(1,'user1@domain.com', '2014-12-12','2016-04-08 12:34:54'),
(2,'user2@domain.com', '2014-12-12','2017-02-13 11:46:53'),
(3,'user3@domain.com', '2014-12-13','2017-04-04 05:12:07');
```

#### Вывод ошибки:

![](/LabW4/ErrorMessages/1.png)

#### Причина ошибки:

Ошибка синтаксиса, требуется как минимум разделение с помощью точкой с запятой

### Задание №2

create table users (
id int(10) unsigned,
email varchar (100),
date_joined date,
last_activity datetime
);
insert into users (id, email, date_joined,last_activity)
values
(1,'user1@domain.com', '2014-12-12','2016-04-08 12:34:54'),
(2,'user2@domain.com', '2014-12-12','2017-02-13 11:46:53'),
(3,'user3@domain.com', '2014-12-13','2017-04-04 05:12:07');
Создайте таблицу calendar для хранения календаря посетителей.
В таблице должны быть следующие поля:

id – идентификатор записи в календаре, целое положительное;
user_id – идентификатор пользователя, целое положительное;
doctor_id – идентификатор доктора, целое положительное;
visit_date – дата и время визита (точность до секунд).

![](/LabW4/5379620308778087126.jpg)

#### Неверное решение:

``` sql
Create table calendar (
id int unsigned,
user_id int unsigned,
doctor_id int unsigned,
visit_date datetime);
Insert into calendar (id, user_id, doctor_id, visit_date)
Values (1, 1914 , 1, '2017-04-08 12:00:00'),
(2, 12, 1, '2017-04-08 12:30:00'),
(3, 4641, 2, '2017-04-09 09:00:00'),
(4, 4641, 2,'2017-04-09 09:00:00'),
(5, 15, 2,'2017-04-09 10:00:00')
```

#### Правильное решение:

``` sql
Create table calendar (
id int unsigned,
user_id int unsigned,
doctor_id int unsigned,
visit_date datetime);
Insert into calendar (id, user_id, doctor_id, visit_date)
Values 
(1, 1914 , 1, '2017-04-08 12:00:00'),
(2, 12, 1, '2017-04-08 12:30:00'),
(3, 4641, 2, '2017-04-09 09:00:00'),
(4, 784, 1,'2017-04-08 13:00:00'),
(5, 15, 2,'2017-04-09 10:00:00')
```

#### Заметка:

VARCHAR (65535) - максимум, если больше 65535, то использовать TEXT

#### Вывод ошибки:

Отсутствует

#### Причина ошибки:

Отсутствует, только исправление оформления

### Задание №3

Создайте таблицу users , в которой будут следующие поля:

id — идентификатор, целые положительные числа.
first_name— имя, строки до 50 символов.
last_name — фамилия, строки до 60 символов.
bio — биография, текст до 65000 символов.

![](/LabW4/5379620308778087125.jpg)

#### Неверное решение:

``` sql
create table users (
id int (10) unsigned,
first_name varchar (50) unsigned,
last_name varchar (60) unsigned,
bio text
);
INSERT INTO users (id, first_name, last_name, bio)
VALUES
(1,'Антон','Кулик','С отличием окончил 39 лицей.'),
(2,'Сергей','Давыдов',''),
(3,'Дмитрий','Соколов','Профессиональный программист.')
```

#### Правильное решение:

``` sql
create table users (
id int (10) unsigned,
first_name varchar (50),
last_name varchar (60),
bio text
);
INSERT INTO users (id, first_name, last_name, bio)
VALUES
(1,'Антон','Кулик','С отличием окончил 39 лицей.'),
(2,'Сергей','Давыдов',''),
(3,'Дмитрий','Соколов','Профессиональный программист.')
```

#### Вывод ошибки:

![](/LabW4/ErrorMessages/3.png)

#### Причина ошибки:

Ошибка синтаксиса, varchar не может быть unsigned

## Лабораторная работа №5 [04.04.2025]

### Задание №1

Выберите из таблицы orders 4 самых дорогих заказов за всё время.
Данные нужно отсортировать в порядке убывания цены.
Отмененные заказы не учитывайте.

![](/LabW5/0_1.jpg)

``` sql
select * from orders where status != "cancelled" order by sum desc limit 4
```

### Задание №2

Выберите из таблицы products название и цены четырех самых дешевых товаров, которые есть на складе.

![](/LabW5/0_2.jpg)

``` sql
select name, price from products where count != 0 order by price limit 4
```

### Задание №3

Выберите из таблицы orders три последних заказа (по дате date) стоимостью от 3200 рублей и выше.
Данные отсортируйте по дате в обратном порядке.

![](/LabW5/0_3.jpg)

``` sql
select * from orders where sum >= 3200 order by date desc limit 3
```

### Задание №4

Создайте данную таблицу:

![](/LabW5/0_4.jpg)

``` sql
DROP TABLE IF EXISTS products;
CREATE TABLE products (
    id INT UNSIGNED NOT NULL,
    name VARCHAR(255) NULL,
    count INTEGER NULL,
    price INTEGER NULL
);
INSERT INTO products (id, name, count, price)
VALUES
    (1, 'Стиральная машина', 5, 10000),
    (2, 'Холодильник', 0, 10000),
    (3, 'Микроволновка', 3, 4000),
    (4, 'Пылесос', 2, 4500),
    (5, 'Вентилятор', 0, 700),
    (6, 'Телевизор', 7, 31740),
    (7, 'Тостер', 2, 2500),
    (8, 'Принтер', 4, 3000),
    (9, 'Активные колонки', 1, 2900),
    (10, 'Ноутбук', 4, 36990),
    (11, 'Посудомоечная машина', 0, 17800),
    (12, 'Видеорегистратор', 23, 4000),
    (13, 'Смартфон', 8, 12300),
    (14, 'Флешка', 4, 1400),
    (15, 'Блендер', 0, 5500),
    (16, 'Газовая плита', 5, 11900),
    (17, 'Клавиатура', 3, 1800);
```

### Задание №5

Из этой таблицы сделать выборку на основе задания: Сайт выводит товары по 5 штук. Выберите из таблицы products товары, которые пользователи увидят на 3 странице каталога при сортировке в порядке возрастания цены (price).

``` sql
select * from products order by price limit 10,5
```
