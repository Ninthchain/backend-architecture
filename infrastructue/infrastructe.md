# Infrastructre folder

В этой папке находится функционал web API нашего микросервиса. Здесь пишутся "ручки"(по хорошему называется контроллер), бизнес-логика и работа с БД

Flow приложения:

Client -> Controller -> Service -> Repository
Client <- Controller <- Service <- Repository
В некоторых случаях не будет использоваться репозиторий, а другой Сервис