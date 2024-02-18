---
description: NOT NULL, UNIQUE, CHECK, DEFAULT, PRIMARY KEY,  FOREIGN KEY
---

# Констрейты

{% hint style="info" %}
**Ограничения (constraints) в SQL** — это инструменты, которые позволяют ограничить или задать правила для данных, хранящихся в таблицах баз данных. Эти ограничения могут быть применены к одному или нескольким столбцам в таблице и обеспечивают целостность данных и защиту от ошибок ввода.
{% endhint %}

## NOT NULL

Ограничение NOT NULL в SQL определяет, что значение в столбце не может быть NULL. Если попытаться вставить NULL значение в столбец с ограничением NOT NULL, то будет выдана ошибка.

<details>

<summary>Пример SQL</summary>

```sql
//Создание таблицы
CREATE TABLE users
(
id int PRIMARY KEY,
name varchar(50) NOT NULL,
email varchar(50) NOT NULL 
);

//Изменение таблицы
ALTER TABLE users ALTER COLUMN name SET NOT NULL;
```

</details>

## UNIQUE <a href="#unique" id="unique"></a>

Ограничение уникальности **(UNIQUE)**  в SQL определяет, что значения в столбце должны быть уникальными. Значения в столбце могут быть NULL, но не более одного NULL значения разрешено.

<details>

<summary>Пример SQL</summary>

```sql
//Создание таблицы
CREATE TABLE users 
( 
id int PRIMARY KEY,
name varchar(50),
email varchar(50) UNIQUE 
);

//Изменение таблицы
ALTER TABLE users ADD CONSTRAINT email_unique_constraint UNIQUE (email);
```

</details>

## CHECK

Ограничение CHECK в SQL определяет условие, которое должно быть выполнено для всех значений в столбце. Если значение не соответствует условию, то будет выдана ошибка.

<details>

<summary>Пример SQL</summary>

```sql
//Создание таблицы
CREATE TABLE employees
( 
id int PRIMARY KEY,
name varchar(50),
salary decimal(10, 2) CHECK (salary > 0) 
);

//Изменение таблицы
ALTER TABLE employees ADD CONSTRAINT salary_constraint CHECK (salary > 0);
```

</details>

## DEFAULT <a href="#default" id="default"></a>

Ограничение DEFAULT в SQL позволяет установить значение по умолчанию для столбца в таблице базы данных. Если при вставке новой строки в таблицу не указано значение для столбца, то будет использоваться значение по умолчанию.

<details>

<summary>Пример SQL</summary>

```sql
//Создание таблицы
CREATE TABLE employees
(
id int PRIMARY KEY,
name varchar(50),
salary decimal(10, 2) DEFAULT 5000.00
);

//Изменение таблицы
ALTER TABLE employees ALTER COLUMN salary SET DEFAULT 5000.00;
```

</details>

## PRIMARY KEY <a href="#primary-key" id="primary-key"></a>

Ограничение первичного ключа **(PRIMARY KEY)** в SQL определяет уникальный идентификатор для каждой строки в таблице. Значения в столбце PRIMARY KEY должны быть уникальными и не могут быть NULL.

<details>

<summary>Пример SQL</summary>

```sql
//Создание таблицы
CREATE TABLE users 
( 
id int PRIMARY KEY,
name varchar(50),
email varchar(50)
);

//Изменение таблицы
ALTER TABLE users ADD PRIMARY KEY (id);
```

</details>

## FOREIGN KEY <a href="#foreign-key" id="foreign-key"></a>

Ограничение внешнего ключа **(FOREIGN KEY)**  в SQL определяет связь между двумя таблицами, где значения в столбце ссылки FOREIGN KEY соответствуют значениям в столбце PRIMARY KEY в другой таблице. Ограничение FOREIGN KEY помогает гарантировать целостность данных, обеспечивая, что ссылочные значения существуют в связанной таблице.

<details>

<summary>Пример SQL</summary>

```sql
//Создание таблицы
CREATE TABLE users 
( 
id int PRIMARY KEY,
name varchar(50),
address_id int,
FOREIGN KEY (address_id) REFERENCES addresses(id)
); 

CREATE TABLE addresses 
( 
id int PRIMARY KEY,
street varchar(50),
city varchar(50),
state varchar(50) 
);

//Изменение таблицы
ALTER TABLE users ADD CONSTRAINT address_id_foreign_key_constraint FOREIGN KEY (address_id) REFERENCES addresses(id);
```

</details>







Источники:

* [https://itonboard.ru/analysis/data\_analysis/370-ogranicheniia\_v\_sql/](https://itonboard.ru/analysis/data\_analysis/370-ogranicheniia\_v\_sql/)
