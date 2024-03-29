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

Подробнее остановимся на DML-командах с которыми, по большей степени приходиться работать аналитику и вскользь пройдемся по DDL/DCL/TCL-командам.







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
