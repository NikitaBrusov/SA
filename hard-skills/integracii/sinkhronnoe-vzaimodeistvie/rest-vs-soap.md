# REST vs SOAP

<table><thead><tr><th width="163"></th><th>REST API</th><th>SOAP API</th></tr></thead><tbody><tr><td>Определение</td><td>Архитектурный стиль</td><td>Протокол</td></tr><tr><td>Формат данных</td><td>JSON</td><td>XML</td></tr><tr><td>Протокол</td><td>HTTP/HTTPS</td><td>HTTP/HTTPS, SMTP, XMPP, и другие</td></tr><tr><td>Описание интерфейса</td><td>Необязательно. <br>Часто используют OpenAPI (Swagger)</td><td>Обязательно. <br>Стандартизация с помощью WSDL (Web Services Description Language)</td></tr><tr><td>Сложность</td><td>Считается более простым и легковесным, поскольку он не требует сложных структур и форматов сообщений</td><td>Cложнее из-за использования XML, где сообщения состоят из заголовков (headers) и тела (body)</td></tr><tr><td>Состояния</td><td>RESTful архитектура является без состояния (stateless), что означает, что каждый запрос от клиента содержит всю необходимую информацию для его обработки</td><td>Может использовать состояние и сохранять контекст между запросами</td></tr></tbody></table>







Источник: [https://habr.com/ru/companies/otus/articles/737610/](https://habr.com/ru/companies/otus/articles/737610/)
