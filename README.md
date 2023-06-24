# Практические

## Практическая работа №2: Простые запросы с SELECT

Базовая структура запроса в PostgreSQL:
SELECT ...
FROM ...
WHERE ...
GROUP BY ...
HAVING ...
ORDER BY ...
LIMIT ...
Написать запросы для базы данных Northwind:
заказчики (клиенты) - customers,
заказы - orders,
вес груза - freight,
поставщики - suppliers,
работники - employees.

====================================================================

1. Посчитать количество заказчиков.

2. Посчитать количество уникальных стран в которых "зарегистрированы" заказчики.

3. Выбрать все заказы из стран France, Austria, Spain.

4. Найти среднее значение дней уходящих на доставку с даты формирования заказа в USA.

5. Найти сумму, на которую имеется товаров (кол-во * цену) причём таких, которые планируется продавать и в будущем (см. на поле discontinued=0).

6. Выбрать все записи заказов в которых наименование страны отгрузки начинается с 'U'.

7. Выбрать записи заказов (включить колонки идентификатора заказа, идентификатора заказчика, веса и страны отгрузки), которые должны быть отгружены в страны имя которых начинается с 'N', отсортировать по весу (по убыванию) и вывести только первые 5 записей.

8. Подсчитать количество заказчиков регион которых известен.

9. Подсчитать количество поставщиков в каждой из стран и отсортировать результаты группировки по убыванию количества.

10. Подсчитать суммарный вес заказов (в которых известен регион) по странам, затем отфильтровать по суммарному весу (вывести только те записи где суммарный вес больше 2750) и отсортировать по убыванию суммарного веса.

11. Выбрать такие страны в которых "зарегистрированы" одновременно и заказчики и поставщики и работники.

12. Выбрать такие страны в которых "зарегистрированы" одновременно заказчики и поставщики, но при этом в них не "зарегистрированы" работники.

## Практическая работа №3: Соединения (JOINS)

В данной работе для соединения таблиц необходимо применять один из операторов JOIN (inner join, left join, right join, full join).

Написать запросы для БД Northwind:

Найти заказчиков и обслуживающих их заказы сотрудников таких, что и заказчики и сотрудники из города London, а доставка идёт компанией Speedy Express. Вывести компанию заказчика (company_name) и ФИО сотрудника (last_name, first_name).
Найти активные (см. поле discontinued=0) продукты из категории Beverages и Seafood, которых в продаже менее 20 единиц (units_in_stock). Вывести наименование продуктов, количество единиц в продаже, имя контакта поставщика (contact_name) и его телефонный номер (phone).
Найти заказчиков, не сделавших ни одного заказа. Вывести имя заказчика (company_name) и order_id (так как заказы не были сделаны, в этом столбце должно быть выведено NULL).

## Практическая работа №4: Подзапросы

Написать запросы для БД Northwind (используя подзапросы):

Вывести продукты количество которых в продаже меньше самого минимального среднего количества продуктов в деталях заказов (группировка по product_id). Результирующая таблица должна иметь колонки product_name и units_in_stock.
Напишите запрос, который выводит общую сумму веса грузов (freight) заказов для компаний-заказчиков для заказов, вес груза которых больше или равен средней величине веса всех заказов, а также дата отгрузки заказа должна находится во второй половине июля 1996 года. Результирующая таблица должна иметь колонки customer_id и freight_sum, строки которой должны быть отсортированы по сумме веса грузов заказов.
Напишите запрос, который выводит 3 заказа с наибольшей стоимостью, которые были созданы после 1 сентября 1997 года включительно и были доставлены в страны Южной Америки (Аргентина, Бразилия, Венесуэла). Общая стоимость рассчитывается как сумма стоимости деталей заказа с учетом дисконта. Результирующая таблица должна иметь колонки customer_id, ship_country и order_price, строки которой должны быть отсортированы по стоимости заказа в обратном порядке.

## Практическая работа №5: DDL - управляем БД и таблицами

create or replace - создать или перезаписать объект (таблицу)
insert into - (вставка данных в таблицу)
alter table - редактировать структуру объекта (таблицы)
add column - добавить столбец
drop column - удалить столбец
rename column -переименовать столбец
alter column - изменить столбец
set data type - изменить тип столбца

Напишите SQL код, который реализует следующие действия:
1. Создать тестовую базу данных (test_db).
2. Создать в ней таблицу  teacher с полями:
- идентификатор учителя (автоинкремент)
- фамилия (lastname)
- имя (firstname)
- день рождения (birthday)
- телефон (phone - тип данных character varying)
3. Добавить в таблицу колонку отчество (secondname).
4. Удалить эту колонку.
5. Переименовать колонку день рождения (birthday->birth_date).
6. Установить длину поля phone в 11 символов.
7. Создать таблицу exam с полями:
- идентификатора экзамена - автоинкрементируемый, уникальный, запрещает NULL;
- наименования экзамена
- даты экзамена
8. Добавить 3-5 записей в таблицу exam.
9. Удалить ограничение уникальности с поля идентификатора.
10. Добавить ограничение первичного ключа на поле идентификатора.
11. Создать таблицу person с полями:
- идентификатора личности (простой int, первичный ключ)
- имя
- фамилия
12. Создать таблицу паспорта (passport) с полями:
- идентификатора паспорта (простой int, первичный ключ)
- серийный номер (простой int, запрещает NULL)
- регистрация (страна и город)
- ссылка на идентификатор личности (внешний ключ)
13. Создать таблицу student с полями:
- идентификатора (автоинкремент)
- фамилия
- имя
- отчество
- курс (по умолчанию 1)
14. Вставить запись в таблицу студентов и убедиться, что ограничение на вставку значения по умолчанию работает.
15. Удалить ограничение "по умолчанию" из таблицы студентов.
16. Вставить еще одну запись в таблицу студентов и убедиться, что ограничение "по умолчанию" отключено.
17. Подключиться к БД "Northwind" (нажать правой кнопкой мыши на базе Northwind и выбрать Query Tool) и добавить ограничение на поле unit_price таблицы products (цена должна быть строго больше 0).
18. "Навесить" автоинкрементируемый счётчик (создать новый sequences) на поле product_id таблицы products (БД Northwind). Счётчик должен начинаться с числа следующего за максимальным значением по этому столбцу (Подсказка: в sequences выставить start with, потом полю product_id переназначить по умолчанию созданный вами sequences ).
19. Произвести вставку в products (не вставляя идентификатор явно) и убедиться, что автоинкремент работает. Вставку сделать так, чтобы в результате команды вернулось значение, сгенерированное в качестве идентификатора.

## Практическая работа №6: Представления (Views)

Структура создания представления:
create view имя_представления
as
(запрос)
ЗАДАНИЕ

Создать представления (view) для БД Northwind:

1. Создать представление, которое выводит следующие колонки:

order_date, required_date, shipped_date, ship_postal_code, company_name, contact_name, phone, last_name, first_name, title из таблиц orders, customers и employees.

Сделать select к созданному представлению, выведя все записи, где order_date больше 1-го января 1997 года.

2. Создать представление, которое выводит следующие колонки:

order_date, required_date, shipped_date, ship_postal_code, ship_country, company_name, contact_name, phone, last_name, first_name, title из таблиц orders, customers, employees.

Попробовать добавить к представлению (после его создания) колонки ship_country, postal_code и reports_to. Убедиться, что происходит ошибка. Переименовать представление и создать новое уже с дополнительными колонками.

Сделать к нему запрос, выбрав все записи, отсортировав их по ship_county.

Удалить переименованное представление.

3.  Создать представление "активных" (discontinued = 0) продуктов, содержащее все колонки. Представление должно быть защищено от вставки записей, в которых discontinued = 1.
(Подсказка: защита представления от "ненужных" вставок осуществляется через команду with local check option добавленную в конец представления)

Попробовать сделать вставку записи с полем discontinued = 1 - убедиться, что не проходит.

4*. Создать представление "Премия за 1997". Вывести список всех сотрудников и информацию заслужили ли они премию по итогам 1997 года. Премия выдается, если количество заказов за год превышает 60.

Результат:

![image](https://github.com/daniilboyarinkov/db-semester-answers/assets/89917619/ebe550bb-c851-46c4-86bf-70da56bc4393)

## Практическая работа №7: CASE, COALESCE, NULLIF

CASE - представляет собой общее условное выражение, напоминающее операторы if/else в других языках программирования:

CASE выражение
    WHEN значение THEN результат
    [WHEN ...]
    [ELSE результат]
END

или второй вариант
CASE WHEN условие THEN результат
     [WHEN ...]
     [ELSE результат]
END
COALESCE - возвращает первый попавшийся аргумент, отличный от NULL. Если же все аргументы равны NULL, результатом тоже будет NULL

COALESCE (discount, 0) - возвращает discount, если discount = NULL , тогда 0

NULLIF(x,y) - выдает значение NULL, если x=y; в противном случае возвращает x

NULLIF(order_id, 11011) - выводи номер заказа (order_id), если заказ номер 11011 тогда выведи NULL

Написать запросы для БД Northwind (используя одну из вышеописанных команд):
Выполните следующий SQL-код (записи необходимы для тестирования корректности выполнения задания):

insert into customers (customer_id, contact_name, city, country, company_name)
values
('AAAAA', 'Alfred Mann', NULL, 'USA', 'fake_company'),
('BBBBB', 'Alfred Mann', NULL, 'Austria','fake_company'),
('CCCCC', 'Alfred Mann', 'Moscow', 'Russia', 'fake_company'),
('DDDDD', 'Alfred Mann', 'Abakan', 'Russia','fake_company');

После этого выполните задание:

1. Вывести имя контакта заказчика (contact_name), его город и страну, отсортировав по возрастанию по имени контакта и городу, а если город равен NULL, то по имени контакта и стране. Проверить результат, используя заранее вставленные строки.

2. Вывести наименование продукта, цену продукта и столбец со значениями:

'too expensive' если цена >= 100
'average' если цена >=50 но < 100
'low price' если цена >=25 но < 50
'very cheap' если цена < 25

3. Найти заказчиков, не сделавших ни одного заказа. Вывести имя заказчика (company_name) и значение 'no orders' если order_id = NULL.

4. Вывести ФИО сотрудников и их должности. В случае если должность = 'Sales Representative' вывести вместо неё 'Sales Stuff'.

## Практическая работа №8: Функции SQL и plpgsql

Общий синтаксис описания функций в PostgreSQL:

1) Если функция стандартная (sql)

create function имя_функции (переменные)

returns тип_данных

as

$BODY$

sql-запросы

$BODY$

language sql

2) Если функция, использующая расширенный функционал PostgreSQL

create function имя_функции (переменные)

returns тип_данных

as

$BODY$

declare переменные

begin

тело функции

end;

$BODY$

language plpgsql

Для БД Northwind создайте следующие функции:

1. Функция, которая выводит число невыполненных заказов (shipped_date is null).

2. Функция, которая выводит для каждой категории границы цен продуктов (минимальную цену товара в категории и максимальную цену товара в этой же категории).

3. Функция, которая выводит всех клиентов (customers_id, company_name) из страны, которая заданна пользователем (country - параметр).

4. Функция, которая для четных category_id (2,4,6,8) пересчитывает цену товаров (unit_price) увеличивая ее в 1,8 раза, а для нечетных category_id (1,3,5,7) уменьшает в 1,5 раза.

Внимание! Функция НЕ должна изменять цену товаров в базовой таблице products, она должна пересчитывать цену товара только внутри себя.

5. Функция, которая выводит минимальную и максимальную зарплату сотрудников для определенного города вводимого пользователем (city - параметр).

Для выполнения данной функции необходимо заранее добавить столбец salary в таблице employees и задать значения.

6. Функция, которая увеличивает зарплату (salary) в таблице employees на заданный процент (процент - параметр функции).

Тут необходимо применить внутри функции команду UPDATE для изменения столбца salary.

## Практическая работа №9: Ошибки и их обработка

Эта практическая работа не связана с базой данных Northwind.

Команда RAISE [level] 'сообщение' - предназначена для вывода сообщений и вызова ошибок.

Существует несколько вариантов (уровней) вызова команды RAISE:

RAISE DEBUG - отладка

RAISE LOG - лог

RAISE INFO - информация

RAISE NOTICE - замечание

RAISE WARNING - потенциальная опасность

RAISE EXCEPTION - исключение / ошибка (прерывает текущую транзакцию)


Задание:
Необходимо написать функцию, которая будет по заданным параметрам (текущая цена товара, минимальная цена товара,
максимальная цена товара, процент увеличения) определять возможно ли провести увеличение цены товара на
определенную величину. Далее модифицировать эту функцию, чтобы запретить (выбрасывая исключения) передачу
аргументов так, что:
- (1) минимальная цена товара превышает максимальную,
- (2) ни минимальная, ни максимальная цена товара не могут быть меньше нуля,
- (3) цена товара после увеличения превышает максимальную,
- (4) коэффициент повышения цены товара не может быть ниже 10% (0.1).

Внимание! Не используйте значок % в выводе сообщения, PostgreSQL считает его спец. символом и это приводит к ошибке при сборке функции.

Необходимо протестировать реализацию, передавая следующие значения аргументов
(cur - текущая цена товара,
min - минимальная цена товара,
max - максимальная цена товара,
pr - процент увеличения).

В итоге функция или выбрасывает сообщение об ошибке, или выводит новую (пересчитанную) цену товара.

Тестовые данные:
cur = 5000, min = 10000, max = 8000, pr = 0.25 (нельзя min>max - нарушение (1))
cur = 5000, min = -1000, max = 1000, pr = 0.2 (нельзя max<0 - нарушение (2-3))
cur = 5000, min = 1000, max = 6000, pr = 0.05 (нельзя pr<0.1 - нарушение (4))
cur = 5000, min = 2000, max = 8000, pr = 0.3 (можно = 6500)
cur = 5000, min = 2000, max = 6000, pr = 0.3 (нельзя - нарушение (3))

## Практическая работа №10: Триггеры

Когда функция на PL/pgSQL срабатывает как триггер, в блоке верхнего уровня автоматически создаются несколько специальных переменных:

NEW - Тип данных RECORD. Переменная содержит новую строку базы данных для команд INSERT/UPDATE в триггерах уровня строки. В триггерах уровня оператора и для команды DELETE эта переменная имеет значение null.

OLD - Тип данных RECORD. Переменная содержит старую строку базы данных для команд UPDATE/DELETE в триггерах уровня строки. В триггерах уровня оператора и для команды INSERT эта переменная имеет значение null.

TG_OP - Тип данных text. Строка, содержащая INSERT, UPDATE, DELETE или TRUNCATE, в зависимости от того, для какой операции сработал триггер.

и другие.

Структура триггеров:

1) Создаем триггерную функцию

create function имя_триггерной_функции() returns trigger as
$BODY$
begin
тело функции
RETURN [NEW/OLD];
end;
$BODY$
language plpgsql

2) Создаем триггер

create trigger имя_триггера [before/after] insert or update or delete
on имя_таблицы
for each row
execute FUNCTION имя_триггерной_функции();

Задание:

Для каждого задания разработать систему триггеров для базы данных Northwind.

1. Для таблицы сотрудники (employees) создать систему триггеров, чтобы для поля учтивое_обращение (title_of_courtesy) при вставке новых данных или редактирования старых можно было внести только четыре определенных значения (Ms., Mrs., Mr., Dr.). Удалять эти данные запрещено.

2. Для таблицы продукты (products) записывать все изменения цен товаров в специальную таблицу аудита (products_audit). Необходимо записывать название товара (product_name), старую и новую цену товара, дату изменения.

3** (для ИКИТ обязательно, для остальных по желанию) Разработать систему триггеров для таблиц products , orders и order_details. При вводе нового заказа в таблицу orders и order_details должно проверяться, есть ли достаточное количество (units_in_stock) этого товара в таблице products, если есть то данные заказа вносятся и количество товаров в заказах (units_on_order) увеличивается. Если товара на складе недостаточно, тогда заказ выводит сообщение об ошибке. Продавать товар, которого нет в достаточном количестве на складе уже нельзя.

## Практическая работа №11: Права доступа

Для большинства типов объектов в исходном состоянии только владелец (или суперпользователь postgres) может делать с объектом всё, что угодно. Чтобы разрешить использовать его другим ролям (пользователям), нужно дать им права. Существует несколько типов прав: SELECT, INSERT, UPDATE, DELETE, TRUNCATE, REFERENCES, TRIGGER, CREATE, CONNECT, TEMPORARY, EXECUTE и USAGE. Набор прав, применимых к определённому объекту, зависит от типа объекта.
Для назначения прав применяется команда GRANT.
GRANT список_прав ON объект TO роль/пользователь;
Все команды настройки прав доступа выполняются от имени супер-пользователя postgres.
Задание:
Для базы данных Northwind настройте права доступа для созданных пользователей.
Продемонстрируйте работы всех пользователей с базой данных Northwind.
1. Создайте 4 новых пользователей: начальник, работник_отдела_кадров, менеджер, работник_склада (boss, personnel, manager, warehouse), для каждого создайте пароль.
2. Настройте права доступа для новых пользователей:
2а. Права доступа для работника_отдела_кадров (personnel):
- Доступ к таблице employees, может добавлять новых сотрудников и редактировать старых. Удалять не может.
2b. Права доступа для работника_склада (warehouse):
- Доступ к таблице products, может добавлять новые продукты и редактировать поле unit_in_stock.
- Доступ к таблице categories, может добавлять категории.
2с. Права доступа для менеджера (manager):
- Доступ к таблицам orders, order_details, customers. Может вносить новые данные заказов (orders, order_details) и новых клиентов (customers), а также редактировать данные заказов.
2d. Права доступа для начальника (boss):
- Доступ к таблице employees, может только удалять (уволить) сотрудников.
- Доступ к таблице suppliers, может добавлять, редактировать и удалять данные о поставщиках.
- Доступ к таблице shippers, может добавлять, редактировать и удалять данные о транспортных компаниях.
- Остальные таблицы открыты только на чтение.

## Практическая работа №13*: Оконное приложение

Данная практическая работа предназначена для групп КИ21-20Б, КИ21-21Б, КИ21-22Б.
(Данная работа обязательна, если вы хотите получить шанс на 5 на экзамене)
Остальные могут делать эту работу по желанию.
Задание:
Необходимо создать оконное приложение "Склад" (используя любой язык программирования), которое будет подключаться к серверу PostgreSQL и конкретно к базе Northwind. В оконном приложении необходимо вывести все данные из таблицы products, а также настроить возможность работы с этими данными.
Необходимо создать функцию добавления нового продукта, удаления старого продукта (по id номеру), поиска продукта (продуктов) по нескольким параметра:
- по category_id (номеру категории),
- по product_name (названию продукта),
- по discontinued (продаваемые/приостановленные).

## Практическая работа №14 - Процедуры

Задание:

Напишите процедуру, которая будет находить и копировать все данные vip-клиентов в отдельную таблицу (vip_customers).

Vip-клиентами будут считаться клиенты, которые сделали больше 25 заказов.

Для выполнения задания, в начале необходимо создать таблицу (vip_customers) в базе Northwind. Скопировать необходимо все данные о клиенте (все 11 столбцов в таблице customers)

---

Мой результат: 

![image](https://github.com/daniilboyarinkov/db-semester-answers/assets/89917619/7043cb8e-1b11-40f4-8473-9ea41d7d7a10)

