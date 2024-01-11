# DDL/DCL/TCL

## DDL – Data Definition Language <a href="#ddl-data-definition-language" id="ddl-data-definition-language"></a>

{% hint style="info" %}
**Data Definition Language (DDL)** – это группа операторов определения данных. Другими словами, с помощью операторов, входящих в эту группы, мы определяем структуру базы данных и работаем с объектами этой базы, т.е. создаем, изменяем и удаляем их.
{% endhint %}

### CREATE

```sql
// Создать базу данных database
CREATE DATABASE database

// Cоздать таблицу table
CREATE TABLE table (
    field INT,
    field2 VARCHAR(255),
    field3 INT
)

// Cоздать таблицу table c дополнительными параметрами
CREATE TABLE table (
    field INT PRIMARY KEY,
    field2 VARCHAR(255) NOT NULL,
    field3 INT NOT NULL DEFAULT 18
)    
```

### ALTER

```sql
// Добавить поле field в таблицу table
ALTER TABLE table
ADD field INT NOT NULL

// Переименовать поле field в таблице table
ALTER TABLE table
RENAME COLUMN field TO field_new

// Переименовать таблицу table
ALTER TABLE table
RENAME TO table_new 
```

### DROP

```sql
// Удалить базу данных database
DROP DATABASE database

// Удалить таблицу table
DROP TABLE table

// Удалить столбец field в таблице table
ALTER TABLE table
DROP COLUMN field
```

***

## DCL – Data Control Language <a href="#dcl-data-control-language" id="dcl-data-control-language"></a>

{% hint style="info" %}
**Data Control Language (DCL)** – группа операторов определения доступа к данным. Иными словами, это операторы для управления разрешениями, с помощью них мы можем разрешать или запрещать выполнение определенных операций над объектами базы данных.
{% endhint %}

### GRANT

```sql
// Предоставить пользователю user права на чтение в таблице table
GRANT SELECT ON table TO user

// Предоставить пользователю user права на запись в таблицу table
GRANT INSERT ON table TO user
```

### REVOKE

```sql
// Отозвать у пользователя user права на чтение в таблице table
REVOKE SELECT ON table TO user

// Отозвать у пользователя user права на запись в таблицу table
REVOKE INSERT ON table TO user
```

### DENY

```sql
// DENY > REVOKE
//Запретить пользователю user разрешение на чтение таблицы table 
//независимо от того, какие разрешения этот пользователь мог унаследовать от роли
DENY SELECT ON table TO user
```

***

## TCL – Transaction Control Language <a href="#tcl-transaction-control-language" id="tcl-transaction-control-language"></a>

{% hint style="info" %}
**Transaction Control Language (TCL)** – группа операторов для управления транзакциями. Транзакция – это команда или блок команд (инструкций), которые успешно завершаются как единое целое, при этом в базе данных все внесенные изменения фиксируются на постоянной основе или отменяются, т.е. все изменения, внесенные любой командой, входящей в транзакцию, будут отменены.
{% endhint %}

**Транзакция** — это набор SQL-запросов, выполняемых над данными, которые объединены в атомарную секцию. Это значит, что промежуточные результаты операции не видны для других конкурирующих транзакций — и вся секция будет либо выполнена, либо полностью отменена в случае ошибки.

### BEGIN/COMMIT

```sql
// Выполнение кода текущей транзакции. Например INSERT в таблицу table
BEGIN TRANSACTION
INSERT INTO table (field1, field2)
VALUES ('value_field1', 'value_field2')
COMMIT
```

### BEGIN/ROLLBACK

```sql
// Откатывает текущую транзакцию и отменяет все обновления, сделанные транзакцией
BEGIN TRANSACTION
INSERT INTO table (field1, field2)
VALUES ('value_field1', 'value_field2')
ROLLBACK
```







Источник:

* [https://info-comp.ru/what-is-ddl-dml-dcl-tcl](https://info-comp.ru/what-is-ddl-dml-dcl-tcl)
* [https://sky.pro/media/gruppy-operatorov-sql/](https://sky.pro/media/gruppy-operatorov-sql/)
