# Основные элементы

{% tabs %}
{% tab title="Activity" %}
<table data-header-hidden><thead><tr><th width="106"></th><th width="180"></th><th width="216"></th><th></th></tr></thead><tbody><tr><td>Задача (Task)</td><td></td><td>Задача — действие или операция, у которых нет дальнейшей декомпозиции в рамках бизнесс-процесса.</td><td><img src="../../../../.gitbook/assets/image (6) (1).png" alt="" data-size="original"></td></tr><tr><td></td><td>Пользовательская задача (User Task)</td><td>задача, которую выполняет человек при содействии других людей или программного обеспечения</td><td><img src="../../../../.gitbook/assets/image (9) (1).png" alt="" data-size="original"></td></tr><tr><td></td><td>Сервисная задача (Service Task)</td><td>задача, предназначенная для оказания услуги, которая может являться как web-сервисом, так и автоматизированным приложением</td><td><img src="../../../../.gitbook/assets/image (10).png" alt="" data-size="original"></td></tr><tr><td></td><td>Скрипт задача (Script Task)</td><td>задача, суть которой заключается в выполнении некоторого сценария (или скрипта) - некоторой автоматической операции</td><td><img src="../../../../.gitbook/assets/image (11).png" alt="" data-size="original"></td></tr><tr><td>Подпроцесс</td><td></td><td>Подпроцесс — декомпозированный процесс, в который включено несколько задач.</td><td><img src="../../../../.gitbook/assets/image (12).png" alt="" data-size="original"></td></tr></tbody></table>
{% endtab %}

{% tab title="Event" %}
<table data-header-hidden><thead><tr><th width="120"></th><th width="166"></th><th width="221"></th><th></th></tr></thead><tbody><tr><td>Событие (Event)</td><td></td><td>События — показывает состояние, которое влияет на дальнейшее течение бизнес-процесса или контролирует его</td><td></td></tr><tr><td></td><td>Стартовое событие</td><td>это событие, которое обозначает начало процесса.</td><td><img src="../../../../.gitbook/assets/image (19).png" alt="" data-size="original"></td></tr><tr><td></td><td>Промежуточное событие</td><td>это событие, которое происходит в середине процесса и может вызывать изменение процесса.</td><td><img src="../../../../.gitbook/assets/image (18).png" alt="" data-size="original"></td></tr><tr><td></td><td>Завершающее событие</td><td>это событие, которое означает завершение процесса.</td><td><img src="../../../../.gitbook/assets/image (17).png" alt="" data-size="original"></td></tr></tbody></table>
{% endtab %}

{% tab title="Gateway" %}
<table data-header-hidden><thead><tr><th width="128"></th><th width="153"></th><th width="234"></th><th></th></tr></thead><tbody><tr><td>Шлюз (Gateway)</td><td></td><td>Определяют условия и маршруты, которые регулируют последовательность выполнения задач в бизнес-процессе.</td><td></td></tr><tr><td></td><td>Параллельный шлюз</td><td>Означает, что два процесса исполняются одновременно. Читается как «И»</td><td><img src="../../../../.gitbook/assets/image (20).png" alt="" data-size="original"></td></tr><tr><td></td><td>Эксклюзивный шлюз</td><td>Используют, чтобы обозначить ветвление потока управления на несколько альтернативных потоков, когда процесс зависит от выполнения условия. Читается как «ИЛИ»</td><td><img src="../../../../.gitbook/assets/image (21).png" alt="" data-size="original"></td></tr><tr><td></td><td>Комплексный шлюз</td><td>Применяют, чтобы показать ветвление потока управления на несколько других, когда процесс зависит от выполнения условий. Читается как «И/ИЛИ»</td><td><img src="../../../../.gitbook/assets/image (22).png" alt="" data-size="original"></td></tr></tbody></table>
{% endtab %}

{% tab title="Data" %}
<table data-header-hidden><thead><tr><th width="109"></th><th width="141"></th><th width="248"></th><th></th></tr></thead><tbody><tr><td>Объект данных</td><td></td><td>Показывает, какие объекты сопровождают выполнение процесса. Например, бумажный документ, электронный документ, информацию и так далее.</td><td></td></tr><tr><td></td><td>Документ </td><td>Используется для отображения на диаграмме документов, сопровождающих выполнение процесса. Рядом с блоком размещается наименование документа.</td><td><img src="../../../../.gitbook/assets/image (4).png" alt="" data-size="original"></td></tr><tr><td></td><td>База данных</td><td>Используется для отображения на диаграмме базы данных, сопровождающей выполнение процесса. Рядом с символом размещается наименование базы данных.</td><td><img src="../../../../.gitbook/assets/image (1).png" alt="" data-size="original"></td></tr><tr><td></td><td>Текстовый комментарий</td><td>Выносной символ, предназначенный для нанесения текстовых комментариев.</td><td><img src="../../../../.gitbook/assets/image (3).png" alt="" data-size="original"></td></tr></tbody></table>
{% endtab %}

{% tab title="Flow" %}
<table data-header-hidden data-full-width="false"><thead><tr><th width="98"></th><th width="129"></th><th width="213"></th><th></th></tr></thead><tbody><tr><td>Поток </td><td></td><td></td><td></td></tr><tr><td></td><td>Поток управления</td><td>Показывает, в каком порядке выполняется процесс. Эти стрелки связывают между собой задачи, события и шлюзы.</td><td><img src="../../../../.gitbook/assets/image (7).png" alt="" data-size="original"></td></tr><tr><td></td><td>Поток сообщений</td><td>Показывает передачу сообщений или объектов из одного процесса в другой.</td><td><img src="../../../../.gitbook/assets/image (8).png" alt="" data-size="original"></td></tr><tr><td></td><td>Ассоциация</td><td>Показывает связи объектов данных и баз данных с процессами.</td><td><img src="../../../../.gitbook/assets/image (6).png" alt="" data-size="original"></td></tr></tbody></table>
{% endtab %}

{% tab title="Pool/Lanes" %}
<table data-header-hidden><thead><tr><th width="121"></th><th width="40"></th><th width="226"></th><th></th></tr></thead><tbody><tr><td>Пул</td><td></td><td>Пул предназначен для отображения потока рассматриваемого процесса. Содержимое пула - это и есть тот процесс, диаграмма которого рассматривается. На диаграмме развернутый пул может быть только один.</td><td><img src="../../../../.gitbook/assets/image (3) (1).png" alt="" data-size="original"></td></tr><tr><td>Дорожка</td><td></td><td>Дорожки располагаются внутри пула. Дорожка предназначена для отображения исполнителей задач и подпроцессов процесса BPMN.</td><td><img src="../../../../.gitbook/assets/image (2) (1).png" alt="" data-size="original"></td></tr></tbody></table>
{% endtab %}
{% endtabs %}







Источник:&#x20;

* [https://market.cnews.ru/articles/2023-05-25\_6\_osnovnyh\_elementov\_bpmn](https://market.cnews.ru/articles/2023-05-25\_6\_osnovnyh\_elementov\_bpmn)
* [https://www.businessstudio.ru/wiki/docs/current/doku.php/ru/csdesign/bpmodeling/bpmn\_notation](https://www.businessstudio.ru/wiki/docs/current/doku.php/ru/csdesign/bpmodeling/bpmn\_notation)
