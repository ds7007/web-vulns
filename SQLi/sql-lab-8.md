SQL injection

В oracle атака с помощью UNION немного отилчается от других.

Нужно использовать from dual в конце.

Пример: ' UNION SELECT NULL, NULL FROM DUAL--

Остальное в целом одинаково проходит с предыдущим лабом

https://portswigger.net/web-security/sql-injection/cheat-sheet