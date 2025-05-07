SQL injection

Можно с помощью UNION атаки проверить версию БД и плюс узнать какой язык БД используется.

Для этого пишем:

UNION SELECT @@version, NULL#

Шпаргалку по версиям можно узнать по ссылке:

https://portswigger.net/web-security/sql-injection/cheat-sheet