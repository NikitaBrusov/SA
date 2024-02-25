# Отсутствие состояния (Авторизация)

> для справки: [identifikaciya-autentifikaciya-avtorizaciya.md](../../../../../../qa-for-sa/identifikaciya-autentifikaciya-avtorizaciya.md "mention")

## **Базовая аутентификация (Basic access authentication)**

Наиболее простая схема, при которой username и password пользователя передаются в заголовке Authorization в незашифрованном виде, а в закодированном (base64-encoded).

Обратите внимание, что даже несмотря на то, что ваши учетные данные закодированы, они не зашифрованы! Получить имя пользователя и пароль при базовой аутентификации очень просто. Не используйте эту схему аутентификации на обычном HTTP, а только при использовании HTTPS (HTTP через SSL/TLS).

Запрос при базовой аутентификации выглядит следующим образом:

```
GET / HTTP/1.1
Host: example.org
Authorization: Basic Zm9vOmJhcg==
```

В этом запросе закодированная пара _username:password (Zm9vOmJhcg==)_ передаётся в заголовке Authorization.\
Базовая аутентификация HTTP редко рекомендуется из-за присущих ей уязвимостей безопасности.

## **Дайджест-аутентификация (Digest access authentication)**

Один из общепринятых методов, используемых веб-сервером для обработки учетных данных пользователя веб-браузера. Данный метод отправляет по сети хеш-сумму логина, пароля, адреса сервера и случайных данных, и предоставляет больший уровень защиты, чем базовая аутентификация, при которой данные отправляются в открытом виде.

При этой схеме сервер посылает уникальное значение _nonce_, а браузер передает MD5 хэш пароля пользователя, вычисленный с использованием указанного _nonce_.

<details>

<summary>Без аутентификации</summary>

Запрос клиента (без аутентификации)

<pre><code><strong>GET /dir/index.html HTTP/1.0
</strong>Host: localhost
</code></pre>

Ответ сервера (без аутентификации)

```
HTTP/1.0 401 Unauthorized
Server: HTTPd/0.9
Date: Sun, 10 Apr 2005 20:26:47 GMT
WWW-Authenticate: Digest realm="testrealm@host.com",
                       qop="auth,auth-int",
                       nonce="dcd98b7102dd2f0e8b11d0f600bfb0c093",
                       opaque="5ccc069c403ebaf9f0171e9517f40e41"
Content-Type: text/html
Content-Length: 311
```

</details>

<details>

<summary>С аутентификацией (имя пользователя «Mufasa», пароль «Circle Of Life»)</summary>

Запрос клиента

```markup
GET /dir/index.html HTTP/1.0
Host: localhost
Authorization: Digest username="Mufasa",
                    realm="testrealm@host.com",
                    nonce="dcd98b7102dd2f0e8b11d0f600bfb0c093",
                    uri="/dir/index.html",
                    qop=auth,
                    nc=00000001,
                    cnonce="0a4f113b",
                    response="6629fae49393a05397450978507c4ef1",
                    opaque="5ccc069c403ebaf9f0171e9517f40e41"
```

Ответ сервера (без аутентификации)

```
HTTP/1.0 200 OK
Server: HTTPd/0.9
Date: Sun, 10 Apr 2005 20:27:03 GMT
Content-Type: text/html
Content-Length: 7984
```

</details>

## **API ключи (API Keys)**

Некоторые API используют API ключи для авторизации. API ключ – это длинная уникальная строка содержащая произвольный набор символов, по сути заменяющие собой комбинацию username/password.

В большинстве случаев, сервер генерирует ключи доступа по запросу пользователей, которые далее сохраняют эти ключи в клиентских приложениях. При создании ключа также возможно ограничить срок действия и уровень доступа, который получит клиентское приложение при аутентификации с помощью этого ключа. Этот ключ может быть отправлен как параметр запроса&#x20;

```
GET /something?api_key=abcdef12345
```

или как заголовок

```
GET /something HTTP/1.1
X-API-Key: abcdef12345
```

или как cookie

```
GET /something HTTP/1.1
Cookie: X-API-KEY=abcdef12345
```

API ключи предполагаются быть секретными, т.е. только клиент и сервер знают этот ключ. Поэтому, как и в базовой, аутентификацию с помощью API ключей следует использовать только вместе с другими механизмами безопасности, такими как HTTPS/SSL.

## **Bearer authentication (also called token authentication)**

Аутентификация на предъявителя (также называемая аутентификацией токена) - это схема проверки подлинности HTTP, которая включает токены безопасности, называемые токенами на предъявителя. Имя «Аутентификация на предъявителя» можно понимать как «предоставить доступ носителю этого токена». Токен-носитель - это загадочная строка, обычно генерируемая сервером в ответ на запрос входа в систему. Клиент должен отправить этот токен несколькими способами:

в заголовке авторизации&#x20;

```
GET /resource HTTP/1.1
Host: server.example.com
Authorization: Bearer mF_9.B5f-4.1JqM
```

в теле запроса

```
POST /resource HTTP/1.1
Host: server.example.com
Content-Type: application/x-www-form-urlencoded
              access_token=mF_9.B5f-4.1JqM`
```

как параметр запроса

```
GET /resource?access_token=mF_9.B5f-4.1JqM HTTP/1.1
Host: server.example.com
```







Источники:

* [https://telegra.ph/Vidy-autentifikacii-v-REST-API-10-18-2](https://telegra.ph/Vidy-autentifikacii-v-REST-API-10-18-2)
* [https://blog.restcase.com/4-most-used-rest-api-authentication-methods/](https://blog.restcase.com/4-most-used-rest-api-authentication-methods/)
