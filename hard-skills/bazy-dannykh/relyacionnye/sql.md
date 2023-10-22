# SQL

**SQL** — язык структурированных запросов (SQL, Structured Query Language), который используется в качестве эффективного способа сохранения данных, поиска их частей, обновления, извлечения и удаления из базы данных.

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
// Вывести топ записей
SELECT * FROM table
```

## JOIN

```sql
LEFT/RIGHT
FULL
```

## DELETE / UPDATE / INSERTE

```sql
// Some code
```



Язык структурированных запросов делится на несколько частей (группы операторов) и позволяет:

* определять данные (DDL),
* манипулировать ими (DML),
* контролировать доступ к данным (DCL)
* и управлять транзакциями (TCL).



Источник: [https://sql-academy.org/ru/guide/basic-syntax-sql-query](https://sql-academy.org/ru/guide/basic-syntax-sql-query)
