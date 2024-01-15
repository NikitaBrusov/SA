# Асинхронное взаимодействие

{% hint style="info" %}
**Асинхронное взаимодействие** — это способ организации взаимодействия между компонентами программной системы, при котором отправитель не блокируется и может продолжать выполнение других задач, в то время как операция выполняется или ожидает ответа от получателя. В асинхронной модели отправитель и получатель не ожидают непосредственного завершения операции, а вместо этого используют механизмы обратного вызова или уведомлений для обработки результатов операции, когда они станут доступны.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/Sync (1).jpg" alt="" width="563"><figcaption><p>Асинхронное взаимодействие</p></figcaption></figure>

## Варианты обмена информацией

При синхронном взаимодействии:&#x20;

* _Request-Response_ (Запрос-Ответ)
* _One-Way_ (Односторонний) или _Fire and Forget_ (Отправил и забыл)

При асинхронном взаимодействии:&#x20;

* _Publish-Subscribe_ (Публикация-Подписка) или сокращённо Pub-Sub
* _Point-to-Point_ (Точка-Точка)

В паттернах Pub-Sub и Point-to-Point происходит асинхронное общение через посредника. При реализации таких паттернов у программ появляются возможности:

* осуществлять асинхронный обмен данными (отправитель не блокируется)
* отделять отправителя от получателя (отправитель ничего не знает о получателе)
* выполнять отложенную обработку сообщений. Получателю не нужно быть постоянно активным, можно читать сообщения в удобное время
* делегировать ответственность за маршрутизацию и доставку сообщений третьей стороне
* легко интегрироваться с системами, использующими различные платформы, языки и протоколы связи

## Брокеры сообщений

{% hint style="info" %}
**Message broker** (брокер сообщений) — это промежуточное программное обеспечение, которое обеспечивает асинхронную коммуникацию между различными компонентами системы, позволяя им обмениваться сообщениями. Он служит посредником между отправителем (producer) и получателем (consumer) сообщений, обеспечивая надежную доставку сообщений даже в условиях различных технологических и временных ограничений.
{% endhint %}

Основные компоненты и функции, которые предоставляет message broker:

1. **Очередь сообщений и топик:** Брокер сообщений обеспечивает создание и управление очередью сообщений, где отправители помещают сообщения для последующей обработки или доставки получателям. Очередь гарантирует, что сообщения обрабатываются в порядке их поступления.
2. **Гарантия доставки:** Брокер сообщений обеспечивает надежную доставку сообщений получателям. Он может использовать различные механизмы, такие как подтверждения, переотправка и повторная обработка сообщений, чтобы убедиться, что сообщение будет доставлено, даже если получатель временно недоступен или система перегружена.
3. **Маршрутизация сообщений:** Брокер сообщений может выполнять функцию маршрутизации, определяя, какие сообщения должны быть доставлены конкретным получателям или группам получателей. Это позволяет гибко настраивать и управлять потоком сообщений.
4. **Преобразование сообщений:** Брокер сообщений может выполнять преобразование сообщений между различными форматами данных или протоколами, позволяя отправителям и получателям использовать разные форматы или интерфейсы.
5. **Управление подписками:** Брокер сообщений позволяет компонентам системы подписываться на определенные типы сообщений или каналы коммуникации. Это позволяет гибко настраивать поток сообщений и контролировать, какие компоненты получают какие сообщения.

### Очередь сообщений и топик

Брокер, реализующий шаблон Point-to-Point, ассоциируется с термином Queue (Очередь). Сообщения отправителя попадают в очередь, получатель извлекает сообщения из очереди. После извлечения сообщение становится больше никому не доступными. Данные в очереди хранятся, пока они не будут прочитаны или не истечёт срок их действия.

В Pub-Sub ассоциируется с темой, топиком (Topic). Сообщения попадают в топик. Система распределяет каждое сообщение между всеми подписчиками топика (Broadcast, вещание). Сообщения могут храниться в топике, до тех пор, пока это необходимо для распространения данных между всеми подписчиками.

### Гарантия доставки

Брокер берёт на себя ответственность за доставку сообщений получателям. При этом в цепочке передачи данных возможны сбои, приводящие к потере данных. В зависимости от того, как ведёт себя система при возникновении сбоев, определяются типы гарантий доставки:

*   **At most once (Не более одного раза)**

    Самый простой вариант — отправка в стиле Fire and Forget (Отправил и забыл). Большая часть сообщений доходит до получателя, но часть теряется из-за сбоев.
*   **At least once (Хотя бы один раз)**

    Чтобы все данные достигли цели, могут предприниматься повторные отправки. Хотя бы одна попытка будет успешной. В таком случае сообщения не теряются, но могут дублироваться.
*   **Exactly once (Строго один раз)**

    Самый труднодостижимый вариант —максимальная гарантия доставки. Сообщения никогда не теряются и не дублируются, каждое доставляется ровно один раз.

### Когда использовать брокеры?

* существуют задачи, выполнение которых требует много времени и ресурсов
* не нужен немедленный результат
* необходима координация работы большого количества сервисов (событийная модель общения)
* требуется повысить масштабируемость и отказоустойчивость системы. Даже если получатель недоуступен, то продюсер всё равно сможет опубликовать сообщение (но в топик)







Источники:&#x20;

* [https://testengineer.ru/message-broker/](https://testengineer.ru/message-broker/)
* [https://habr.com/ru/companies/innotech/articles/698838/](https://habr.com/ru/companies/innotech/articles/698838/)