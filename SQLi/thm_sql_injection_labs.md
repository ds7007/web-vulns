SQL injection

Cуществует разные виды использования обычных SQL инъекций.

OR 1=1 --

' OR 1=1 --

' OR '1'='1' --

Сначала просто вставляем ' и смотря на то что возвращает сервер делаем вывод и продолжаем.

Если вовращает ошибку типа Syntax error near "'" или Unclosed quotation mark то в поле с кавычками.

Если ошибки нет то строковое

Виды ошибок: 

You have an error in your SQL syntax

Unclosed quotation mark after the character string

Unexpected token '...'

Invalid number format

Символ ' это как зонд для SQL injection

Иногда бывают такие ситуации когда вводишь логин и пароль в самой страничке а он отображается в URL тогда можно инъекцию попробовать ввести и в URL. Иногда сервер запрещает ввести символы в поле.