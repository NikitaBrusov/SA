---
description: XML "Swagger"
---

# WSDL

{% hint style="info" %}
**WSDL (Web Services Description Language)** — это язык описания веб-сервисов, основанный на XML. На нем описываются методы, входные и результирующие структуры данных, типы данных, сетевые адреса для обращения к сервису и другое.

SOAP связан с WSDL по той части, что SOAP обеспечивает транспорт, а WSDL обеспечивает объявление веб-сервиса.
{% endhint %}

## Элементы WSDL

Существуют две версии языка:

* версия 1.1 от 2001 года, [https://www.w3.org/TR/wsdl.html](https://www.w3.org/TR/wsdl.html)
* версия 2.0 от 2007 года, [https://www.w3.org/TR/wsdl/](https://www.w3.org/TR/wsdl/)

Документы WSDL состоят из следующих разделов:

<table data-full-width="true"><thead><tr><th>Раздел</th><th>Версия 1.1</th><th>Версия 2.0</th></tr></thead><tbody><tr><td>&#x3C;definitions></td><td>Задает пространства имен для документа WSDL, XML-схемы и SOAP</td><td>Отсутствует.<br>Вместо него существует раздел &#x3C;description></td></tr><tr><td>&#x3C;description></td><td>Отсутствует.<br>Вместо него существует раздел &#x3C;definitions></td><td>Задает пространства имен для документов WSDL, XML и SOAP</td></tr><tr><td>&#x3C;types></td><td>Элементы (данные), с которыми работает веб-сервис</td><td>Аналогично</td></tr><tr><td>&#x3C;message></td><td>Сообщения, с которыми работает веб-сервис</td><td>Отсутствует</td></tr><tr><td>&#x3C;portType></td><td>Операции, которые могут проводиться с сообщениями из раздела &#x3C;message></td><td>Отсутствует. Вместо него существует раздел &#x3C;interface></td></tr><tr><td>&#x3C;interface></td><td>Отсутствует.<br>См. раздел &#x3C;portType></td><td>Операции, которые могут проводиться с элементами (данными) из раздела &#x3C;types></td></tr><tr><td>&#x3C;binding></td><td>Определение сетевого протокола и формат данных, используемых для операций из раздела &#x3C;portType></td><td>Аналогично</td></tr><tr><td>&#x3C;operation></td><td>Абстрактное определение операции (функции), в которой указываются входящее и исходящее сообщения, а так же сообщение об ошибке.</td><td>Аналогично</td></tr><tr><td>&#x3C;service></td><td>Объединяет конечные точки (адреса), реализующие общий интерфейс веб-сервиса. В разделе указывается общий адрес веб-сервиса</td><td>Аналогично</td></tr><tr><td>&#x3C;port></td><td>Протоколы и адреса, по которым выполняются запросы к веб-сервису</td><td>Отсутствует</td></tr><tr><td>&#x3C;endpoint></td><td>Отсутствует.<br>Вместо него существует раздел &#x3C;port></td><td>Протоколы и адреса, по которым выполняются запросы к веб-сервису</td></tr></tbody></table>







Источники:&#x20;

* [https://yandex.ru/dev/direct/doc/dg-v4/concepts/SOAP.html](https://yandex.ru/dev/direct/doc/dg-v4/concepts/SOAP.html)
* [https://vbeg.ru/tezam/soap-i-wsdl-teoriya/](https://vbeg.ru/tezam/soap-i-wsdl-teoriya/)
* [https://systems.education/soap-integration](https://systems.education/soap-integration) (подробнее)
