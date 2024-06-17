Проект Автотест
Автоматизация чек-листа для поля name в запросе на создание набора в Яндекс Прилавке с помощью API Яндекс Прилавка.
Яндекс Прилавок это учебное web-приложение для практики работы с API, SQL.

Язык приложения — JavaScript.
Доступ к приложению по протоколу HTTP 1.1.
Документация к приложению осуществляется с помощью модуля apiDoc.
Приложение использует базу данных — PostgreSQL.
Требования
Для запуска тестов должны быть установлены пакеты pytest и requests.
Запуск всех тестов выполняется командой pytest.
Чек-лист проверок
№	Описание	ОР
1	Допустимое количество символов (1): kit_body = { "name": "a" }	
Код ответа — 201
В ответе поле name совпадает с полем name в запросе
2	Допустимое количество символов (511): тестовое значение под таблицей	
Код ответа — 201
В ответе поле name совпадает с полем name в запросе
3	Количество символов меньше допустимого (0): kit_body = { "name": "" }	
Код ответа — 400
4	Количество символов больше допустимого (512): тестовое значение под таблицей	
Код ответа — 400
5	Разрешены английские буквы: kit_body = { "name": "QWErty" }	
Код ответа — 201
В ответе поле name совпадает с полем name в запросе
6	Разрешены русские буквы: kit_body = { "name": "Мария" }	
Код ответа — 201
В ответе поле name совпадает с полем name в запросе
7	Разрешены спецсимволы: kit_body = { "name": ""№%@"," }	
Код ответа — 201
В ответе поле name совпадает с полем name в запросе
8	Разрешены пробелы: kit_body = { "name": " Человек и КО " }	
Код ответа — 201
В ответе поле name совпадает с полем name в запросе
9	Разрешены цифры: kit_body = { "name": "123" }	
Код ответа — 201
В ответе поле name совпадает с полем name в запросе
10	Параметр не передан в запросе: kit_body = {}	
Код ответа — 400
11	Передан другой тип параметра (число): kit_body = { "name": 123 }	
Код ответа — 400
Тестовые значения для проверок №2 и №4
Допустимое количество символов (511)

kit_body = { "name": "AbcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdAbcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabC" }
Количество символов больше допустимого (512)

kit_body = { "name": "AbcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdAbcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcdabcD" }
Шаги выполнения проекта
Написать POST-запрос на создание нового пользователя и сохранение токена авторизации authToken.
Написать POST-запрос на создание личного набора для этого пользователя. Учесть передачу заголовка Authorization.
Написать функции для проверки позитивных и негативных сценариев чек-листа.
Запустить автотест.
Упаковать папку с файлами configuration.py, data.py, sender_stand_request.py, create_kit_name_kit_test.py, README.md, .gitignore в ZIP-архив.
Создание пользователя
Тип запроса – POST. Эндпоинт – /api/v1/users.

Успешное создание учётной записи пользователя
HTTP/1.1 201 Created
{
   authToken: 'jknnFApafP4awfAIFfafam2fma'
}
Создание набора внутри конкретной карточки или пользователя
Тип запроса – POST. Эндпоинт – /api/v1/kits.

Заголовок для получения наборов, созданных пользователем
{
   "Content-Type": "application/json",
   "Authorization": "Bearer jknnFApafP4awfAIFfafam2fma"
}
Стек для выполнения проекта
PyCharm

GitHub

requests

pytest

Автор
Астахова Татьяна 19я когорта
