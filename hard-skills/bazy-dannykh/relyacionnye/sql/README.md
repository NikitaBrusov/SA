# SQL

{% hint style="info" %}
**SQL** — язык структурированных запросов (SQL, Structured Query Language), который используется в качестве эффективного способа сохранения данных, поиска их частей, обновления, извлечения и удаления из базы данных.
{% endhint %}

Обращение к реляционным СУБД осуществляется именно благодаря SQL. С помощью него выполняются все основные манипуляции с базами данных, например:

* Извлекать данные из базы данных
* Вставлять записи в базу данных
* Обновлять записи в базе данных
* Удалять записи из базы данных
* Создавать новые базы данных
* Создавать новые таблицы в базе данных
* Создавать хранимые процедуры в базе данных
* Создавать представления в базе данных
* Устанавливать разрешения для таблиц, процедур и представлений

Язык структурированных запросов делится на несколько частей (группы операторов) и позволяет:

* определять данные (DDL[^1]),
* манипулировать ими (DML[^2]),
* контролировать доступ к данным (DCL[^3])
* и управлять транзакциями (TCL[^4]).

Подробнее остановимся на DML-командами с которыми, по большей степени приходиться работать аналитику.&#x20;

## SELECT

```sql
// Вывести всю таблицу table
SELECT * FROM table

// Вывести конкретное поле field
SELECT field FROM table

// Вывести уникальные значени поля field
SELECT distinct field FROM table
```

## WHERE

```sql
// Отфильтровать записи по числовому полю
SELECT * FROM table
WHERE field = 123

// Отфильтровать записи по стринг полю
SELECT * FROM table
WHERE field = 'value'


// Отфильтровать записи по вхождению в стринг поле
SELECT * FROM table
WHERE field LIKE 'value'
```

## ORDER BY

```sql
// Отсортировать записи по возрастанию
SELECT * FROM table
ORDER BY field ASC // ACS необязательно, сортировка по умолчанию = по возрастанию

// Отсортировать записи по возрастанию
SELECT * FROM table
ORDER BY field DESC
```

## GROUP BY

```sql
// Группировка по полю field 
SELECT field FROM table
GROUP BY field
```

## Агрегатные функции

```sql
// AVG
// Среднее значение по полю field
SELECT AVG(field) FROM table
// Среднее значение по полю field, группируя по field2
SELECT field2, AVG(field) FROM table
GROUP BY field2

// SUM
// Сумма значений значение по полю field
SELECT SUM(field) FROM table

// MAX
// Максимальное значение по полю field
SELECT MAX(field) FROM table

// MIN
// Минимальное значение по полю field
SELECT MIN(field) FROM table
```

## LIMIT/TOP

```sql
// PostgreSQL и другие
// Вывести топ 10 записей
SELECT * FROM table
LIMIT 10
// Вывести записи с 5 по 10
SELECT * FROM table
LIMIT 5 OFFSET 4

// MS SQL
// Вывести топ 10 записей
SELECT TOP 10 * FROM table
```

## JOIN

{% code fullWidth="true" %}
```sql
//Внутренее соединение 
//Получение данных, относящихся как к левой, так и к правой таблице.
//INNER JOIN или просто JOIN
SELECT * FROM table1 t1
JOIN table2 t2 ON t1.field1 = t2.field1

//Внешнее соединение
//Получение всех данных из левой таблицы, соединённых с соответствующими данными из правой.
//LEFT JOIN
SELECT * FROM table1 t1
LEFT JOIN table2 t2 ON t1.field1 = t2.field1
//Получение всех данных из правой таблицы, соединённых с соответствующими данными из левой.
//RIGHT JOIN
SELECT * FROM table1 t1
RIGHT JOIN table2 t2 ON t1.field1 = t2.field1
//Получение всех данных, относящихся к левой и правой таблицам, а также их внутреннему соединению.
//FULL OUTER JOIN
SELECT * FROM table1 t1
FULL OUTER JOIN table2 t2 ON t1.field1 = t2.field1
```
{% endcode %}

## Подзапросы

```sql
//Пример1
SELECT field1, (SELECT field1 FROM table2) FROM table1
WHERE field1 = 'value'

//Пример2
SELECT field1 FROM table1
WHERE filed1 = (SELECT field2 FROM table2 WHERE field2 = 'value')
```

## UNION

```sql
//Объедение запросов. Без повторов одинаковых строк. 
SELECT * FROM table1
UNION
SELECT * FROM table2

//Объедение запросов. C повторами одинаковых строк. 
SELECT * FROM table1
UNION ALL
SELECT * FROM table2
```

## INSERT/UPDATE/DELETE|TRUNCATE

{% code fullWidth="true" %}
```sql
//Вставить новую запись в таблицу
INSERT INTO table1 (field1, field2)
VALUES ('value_field1', 'value_field2')

//Изменить старую запись в таблице
UPDATE table1
SET field2 = 'value_field2'
WHERE field1 = 'value'

//Удалить конкретную запись в таблице
DELETE FROM table1
WHERE field1 = 'value'
//Удалить все записи в таблице (записи будут удаляться по одной, пока таблица польностью не очистится)
DELETE FROM table1
//Удалить все записи в таблице (удалится вся таблица со всеми записями, после чего создастся новая пустая)
TRUNCATE FROM table1
```
{% endcode %}







Полезное: &#x20;

* [https://sql-academy.org/ru/guide/basic-syntax-sql-query](https://sql-academy.org/ru/guide/basic-syntax-sql-query)
* [https://sky.pro/media/gruppy-operatorov-sql/](https://sky.pro/media/gruppy-operatorov-sql/)

[^1]: DDL, или Data Definition Language — это группа команд, которые используются для создания и изменения структуры объектов базы данных: таблиц, представлений, схем и индексов.



    Примеры команд: CREATE, ALTER, DROP.

[^2]: DML, или Data Manipulation Language — это группа операторов, которые позволяют получать и изменять записи, присутствующие в таблице.&#x20;



    Примеры команд: SELECT и тд

[^3]: DCL, или Data Control Language — это команды SQL, которые используют для предоставления и отзыва привилегий пользователя базы данных. При этом пользователь не может откатить изменения. &#x20;



    Примеры команд: GRANT и REVOKE

[^4]: TCL, или Transaction Control Language — одни из наиболее популярных команд SQL. Их используют для обеспечения согласованности базы данных и для управления транзакциями. \
    \
    Примеры команд: BEGIN/COMMIT, ROLLBACK
