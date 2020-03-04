Лабораторная работа №7
1.Прибавить к дате data(Sale) 2 месяца, отнять из даты 3 месяца.
2. Вывести названия задач, которые начинаются до 19 мая 2011г.
3. Определить, сколько дней осталось до Рождества.
4. Определить, какой день недели будет послезавтра.
5. Округлить до целого с избытком и недостатком значения столбца cost.
6. Вывести название месяца в датах продаж.
7. Определить сколько лет, месяцев прошло с даты каждой продажи.
8. Вывести фамилии сотрудников.
9.Вывести имена сотрудников.
10. Представить данные столбца m_name в виде firma – название фирмы.
11. Заменить значение null в столбце man_id на значение 0.

ПРИМЕРЫ:
1. Математические функции
select abs(-5) - модуль числа -5
5
select pi() – число пи в радианах
3,14159265358979
select degrees(pi()) – число пи в градусах
180
select sin(30) - синус 30 радиан
-0,988031624092862
select sin(radians(30.0)) – синус 30 градусов
0.5
select log10(100) – десятичный логарифм от 100
2
select floor(3.99) – округление до целого с недостатком
3
select ceiling(3.01) – округление до целого с избытком
4
select round(345.4567,3) – математическое округление до тысячных
345.4570
select round(345.4567,-2) – математическое округление до сотен
300.0000
select round(345.4567,-1) – математическое округление до десятков
350.0000
select round(345.4567,-1,-1) – обрезка числа до десятков
340.0000
select power(2,0.5) возведение числа 2 в степень 0.5
1
select power(-2,0.5)
Error!!!!

2. Функции дата/время 
select getdate()– текущая дата и время
2018-05-22 10:10:36.033

select current_timestamp – текущая дата и время
2018-05-22 10:11:38.960

select sysdatetime()– системная  дата и время
2018-05-22 10:12:44.1492534

select sysutcdatetime()– системная дата и время UTC
2018-05-22 07:14:16.6971246

select sysdatetimeoffset()– системная дата и время с поясом по отношению к UTC
2018-05-22 10:13:29.1579250 +03:00


select day(getdate()) - день
22

select month(getdate()) -месяц
5

select year(getdate()) - год
2018

select datepart(yy, getdate()) - год
2018

select datepart(w, getdate()) – день недели (1 – воскресенье)
3

select datepart(ww, getdate()) - неделя
21

select datename(w, getdate()) –  название дня недели
Tuesday

select isdate(getdate()) – проверка является ли аргумент датой
1

select distinct isdate(sp_name) from sperson - проверка является ли аргумент датой

0

select dateadd(yy, 5, getdate()) – добавить 5 лет к текущей дате
2023-05-22 10:42:31.263

select data, 
datediff(yy, data, getdate()) diference from sale
– разница в годах между текущей датой и датами продаж
from sale
2011-02-28	7
2011-02-12	7
2011-02-15	7
2011-02-02	7
2011-02-05	7
2011-02-22	7
2011-02-14	7
2011-02-01	7
2011-02-04	7

3. Символьные функции
select ascii('A') – код символа 
65

select char(65) – символ по коду
A

select charindex('a', 'mama') – позиция первой буквы «а» в слове «мама»
2

select patindex('%gs%', 'longstring') – позиция символа “g” в слове 'longstring'
4

select left(m_name, 5) from manufact – первые 5 символов
Odejd
Medny
Lampy

select right(m_name, 5) from manufact – последние 5 символов
Kivi"
delia
 Lama

select lower(m_name) from manufact – нижний регистр
odejda "kivi"
mednye izdelia
lampy lama

select upper(m_name) from manufact  - верхний регистр
ODEJDA "KIVI"
MEDNYE IZDELIA
LAMPY LAMA


select ltrim('       as') – удаляет пробелы в начале строки (слева)
as

select nchar(234) – символ Unicode по коду
ê

select unicode('ф') – код символа
1092

select replicate('a',3)
aaa

select replace(m_name, 'i', '*') замена всех “i” на “*”
from manufact
Odejda "K*v*"
Mednye *zdel*a
Lampy Lama

select reverse('abcdef') – обратный порядок
fedcba

select str(3.4567, 4, 2) – преобразование в строку с математическим округлением
3.46

select len(m_name) from manufact – длина строки
13
14
10

select substring(m_name, 3, 5) from manufact - выделяет подстроку, начиная с 3 символа длиной 5 символов
ejda 
dnye 
mpy L

select substring(m_name, 3, len(m_name)) from manufact – выделяет подстроку, начиная с 3 символа и до конца строки
ejda "Kivi"
dnye izdelia
mpy Lama

select stuff('Notebook', 5, 0, ' in a ')
Note in a book

select stuff('Notebook', 1, 4, 'Hand')
Handbook

4. Функции преобразования
select cast(getdate() as varchar(12))
May 22 2

select convert(varchar(12), getdate(), 104)
22.05.2018

select isnull(man_id, 0) from sperson
27
27
44
35
0
27
12
44
27

select current_user
dbo

select isnumeric('bb')
0

select p_desc, nullif(p_desc, 'Sweater') from product
Sweater	NULL
Desc lamp	Desc lamp
Desc lamp	Desc lamp
Bronze sculpture	Bronze sculpture
