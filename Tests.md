Оптимальным кол-вои тестов является проверка каждого возможного ответа согластно спецификации 

[Тест 1] [Success]

Отправляем Request

-POST
-header "Authorization: OAuth anonymousToken", "accept: */*", "Content-Type: application/json"
-body {"login": "login", "password": "password"}

Ожидаем Response

-200
-нет
-{
  "login": "string",
  "token": "string",
  "refreshToken": "string",
  "expiredAt": "2015-07-20T15:49:04-07:00"
}

[Тест 2] [Bad Request]

Отправляем Request

-POST
-header "Authorization: OAuth anonymousToken", "accept: */*", "Content-Type: application/json"
-нет

Ожидаем Response

-400
-нет
-{
  "timestamp": "2022-11-01T07:17:16.236Z",
  "status": 0,
  "error": "string",
  "message": "string"
}


[Тест 3][Unauthorized]

Отправляем Request

-POST
-header "Authorization: OAuth anonymousToken213", "accept: */*", "Content-Type: application/json"
-body {"login": "login", "password": "password"}

Ожидаем Response

-401
-нет
{
  "timestamp": "2022-11-01T07:17:16.238Z",
  "status": 0,
  "error": "string",
  "message": "string"
}

[Тест 4][Not Found] при условии, что есть проверка на наличие такого пользователь

Отправляем Request

-POST
-header "Authorization: OAuth anonymousToken", "accept: */*", "Content-Type: application/json"
-body {"login": "loginME", "password": "password"}

Ожидаем Response

-404
-нет
{
  "timestamp": "2022-11-01T07:17:16.238Z",
  "status": 0,
  "error": "string",
  "message": "string"
}

[Тест 5] [Bad Request]

Отправляем Request

-POST
-header "Authorization: OAuth anonymousToken", "accept: */*", "Content-Type: application/json"
-body {}

Ожидаем Response

-500
-нет
{
  "timestamp": "2022-11-01T08:31:29.906Z",
  "status": 0,
  "error": "string",
  "message": "string"
}
  
