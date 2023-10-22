# Колоночные

**Колоночные базы данных** (Columnar Databases) - это тип баз данных, где данные хранятся и организуются по колонкам, в отличие от традиционных реляционных баз данных, где данные хранятся по строкам. В колоночных базах данных каждая колонка содержит данные одного типа, и они компактно хранятся в сжатом формате.

## Преимущества

* быстрое выполнение запросов на чтение данных
* более эффективное использование памяти, чем в строчных бд
* лучшую сжимаемость данных, чем в строчных бд
* более простая масштабируемость БД
* низкие требования к консистентности данных
* распределенные вычисления и распараллеливание запросов (MPP)
* шардирование данных (хранение по частям на разных хостах)

## Примеры

Некоторые известные колоночные базы данных:&#x20;

* Сlickhouse
* Apache Cassandra
* Vertica

## Где применяются

Колоночные таблицы обычно хорошо подходят для аналитических и OLAP[^1] задач, где требуется обработка больших объемов данных.







Источник: [https://backendinterview.ru/db/column/index.html](https://backendinterview.ru/db/column/index.html)

[^1]: OLAP (OnLine Analytical Processing) — оперативная аналитическая обработка данных или анализ данных в реальном времени.