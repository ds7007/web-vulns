SQL injection Union attack

Нужно проверять каждый NULL чтобы он совпадал с другим значением.
Проверяется это так 
Union select NULL, NULL, NULL

Union select 'a', NULL, NULL

Union select NULL, 'a', NULL

Union select NULL, NULL, 'a'

Если совпадение будет то сайт вернет текс в виде 'a' если не будет совпадений то вернет ошибку