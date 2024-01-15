---
description: Kubernetes (K8s) – автоматизация Docker
---

# Kubernetes

{% hint style="info" %}
**Kubernetes** — это платформа с открытым исходным кодом для управления контейнеризированными рабочими нагрузками (workload) и сервисами. Фактически Kubernetes является оркестратором рабочей нагрузки.
{% endhint %}

## Причины по которым используется **Kubernetes**&#x20;

* Как обеспечить изоляцию нескольких сервисов на одном сервере и удобный запуск? Например, могут быть случаи, когда одно приложение будет занимать большую часть ресурсов, в результате чего другие сервисы будут работать хуже.
* Как при добавлении нового экземпляра сервиса выбрать сервер, на котором достаточно ресурсов для запуска?
* Как гарантировать отсутствие простоев? Если сервис выходит из строя, необходимо его перезапустить. Если вышел из строя сервер, то необходимо запустить те сервисы, которые на нем были, на других машинах.
* Как организовать межсервисное взаимодействие? Как сервисам друг к другу обращаться в условиях динамически меняющейся среды, когда экземпляры сервисов могут "переезжать" с одного сервера на другой?
* Как обеспечить горизонтальное и вертикальное масштабирование сервисов?&#x20;
* Как обеспечить конфигурирование сервисов?
* Как обеспечить обновление приложения новую версию?

## Как работает Kubernetes <a href="#kak-rabotaet-kubernetes" id="kak-rabotaet-kubernetes"></a>

Сами по себе контейнеры — это способ развертывания и запуска приложений на сервере. Если контейнеров несколько, важно настроить их совместную работу так, чтобы они не отбирали друг у друга ресурсы аппаратной платформы и эффективно их расходовали. Кроме развертывания и запуска контейнеров, разработчику нужно периодически исправлять ошибки. Делать это вручную очень сложно. Kubernetes позволяет автоматизировать большинство процессов. Это называется «оркестрация контейнеров». Платформа может масштабировать приложения и обрабатывать возникающие ошибки, распределять ресурсы, поддерживать баланс между контейнерами и т.д. Но K8s работает не один. Чтобы он мог запустить приложения и службы в контейнерах, каждый должен быть оснащен средой выполнения. Это может быть Docker, rkt или runc.

Kubernetes действует на уровне логики, а не аппаратного обеспечения, по принципу «ведущий — ведомый». Управление системой основано на двух подходах:

* **декларативном —** разработчик задает цели, а не пути их достижения, которые система автоматически выбирает сама;
* **императивном —** разработчик может распоряжаться ресурсами с помощью команд «Создать», «Изменить», «Удалить».

## Возможности Kubernetes <a href="#vozmozhnosti-kubernetes" id="vozmozhnosti-kubernetes"></a>

**Наблюдение за работой сервисов.** Платформа позволяет следить как за отдельными приложениями, так и за всем кластером сразу. K8s имеет веб-интерфейс. Все данные о работе сервисов система предоставляет разработчику в интуитивно понятном виде.

**Распределение нагрузки.** Трафик, который потребляют контейнеры, может различаться. Это негативно влияет на развертывание приложений. Kubernetes автоматически отслеживает нагрузку в контейнерах, и если в каком-то из них обнаруживается высокий трафик, то платформа распределяет его между другими контейнерами. Это может сделать и сам разработчик, указав платформе имеющиеся ресурсы, а также их количество, необходимое для работы приложений.

**Оркестрация хранилища.** С помощью Kubernetes разработчик может выбрать систему хранения: локальное хранилище, облако и т.д. Платформа автоматически создаст ее и настроит под потребности проекта.

**Развертывание и откаты.** Платформа позволяет развертывать приложения в автоматическом и ручном режимах. Есть вариант канареечного развертывания, когда изменения, внесенные разработчиком, применяются только на некоторой части контейнеров. Такое решение позволяет осторожно тестировать обновления. Изменения можно автоматически откатить.

**Самоконтроль.** Если контейнер отказывает или сбоит, Kubernetes автоматически перезапускает или останавливает его. Освободившиеся ресурсы она распределяет на другие приложения. Система контролирует их работу в соответствии с критериями, заданными разработчиком. Если контейнер не соответствует им, платформа отключает его или заменяет на другой, а также скрывает от клиента, пока он не будет готов к обслуживанию.

**Безопасность и конфиденциальность.** Kubernetes может сохранять и контролировать конфиденциальные данные (пароли, ключи SSH, OAuth-токены), распределять права доступа к системе. Обновление и развертывание приложений не затрагивает образы контейнеров и не раскрывает секретные сведения в конфигурации стека.

## Архитектура кластера Kubernetes

<figure><img src="../../../../../../.gitbook/assets/osi (11).jpg" alt=""><figcaption><p>Архитектура кластера Kubernetes</p></figcaption></figure>

### Nodes (ноды, узлы)

Это физические или виртуальные машины, на которых развертываются и запускаются контейнеры с приложениями. Совокупность нод образует кластер Kubernetes.

Nodes бывают двух типов:

1. **Master (мастер-нода) —** узел, управляющий всем кластером. Он следит за остальными нодами и распределяет между ними нагрузку с помощью менеджера контроллеров (controller manager) и планировщика (scheduler). Как правило, мастер-нода занимается только управлением и не берет на себя рабочие нагрузки. Для повышения отказоустойчивости существует несколько мастер-нод.
2. **Worker (рабочие ноды) —** узлы, на которых работают контейнеры. В зависимости от параметров ноды (объема памяти и центрального процессора) на одном узле может работать много контейнеров. Чем больше рабочих узлов, тем больше приложений можно запустить. Также количество влияет на отказоустойчивость кластера, потому что при выходе из строя одной ноды нагрузка переносится на другие.

### Pods (Поды)

**Pod, под** — это объект Kubernetes, который является описанием атомарной единицы рабочей нагрузки.  Pod можно воспринимать, как описание запущенного инстанса сервиса или задачи. &#x20;

Это абстрактный объект Kubernetes, представляющий собой «обертку» для одного или группы контейнеров. Контейнеры в поде запускаются и работают вместе, имеют общие сетевые ресурсы и хранилище. Kubernetes не управляет контейнерами напрямую, он собирает их в поды и работает с ими.

Под и все его контейнеры функционируют на одном узле и находятся там до завершения работы. Оно может произойти в соответствии с жизненным циклом, из-за выхода из строя узла или обновления контейнера в составе пода. При пересоздании под может создаться на другой ноде, которая отличается от первоначальной.

Чаще всего в поде только один контейнер (приложение), потому что у каждого могут быть свои требования к масштабированию, производительности, SLA и пр.

Поды, объединяющие несколько контейнеров, встречаются реже. Например, когда надо объединить взаимосвязанные приложения, зависящие друг от друга. Запускать их отдельно бессмысленно.

### Controllers (контроллеры)

Контроллеры — это общее название средств управления, следящих за кластером и поддерживающих желаемое его состояние. Существует несколько типов контроллеров:

* **Deployment (развертывание).** Набор алгоритмов и директив, описывающих поды, число их экземпляров, порядок их замены при изменении характеристик. С его помощью разработчик декларирует изменения нодов и наборов реплик. Это самый популярный способ разместить приложение в Kubernetes.
* **ReplicaSet (набор реплик).** Описывает и управляет работой нескольких подов на кластере. Чем больше таких реплик, тем выше устойчивость системы к отказам и лучше масштабируются приложения.
* **StatefulSet (набор состояния).** Контроллер применяется для управления приложениями с отслеживанием состояния (stateful-приложениями) с использованием постоянного хранилища.
* **DaemonSet** **(набор «демонов»).** Представляет собой совокупность «демонов» (фоновых программ, работающих без взаимодействия с пользователем) и отвечает за запуск одной реплики выбранного пода на каждом отдельном узле. То есть по мере добавления узлов в кластер добавляются и поды.
* **Job (задание).** Контроллер, отвечающий за однократный запуск выбранного пода и завершающий его работу. CronJob — его разновидность, запускающая группу заданий по заданному расписанию.

### Services (сервисы)

Сервисы объединяют поды в логическую группу и определяют политику доступа к ним. По функционалу они напоминают маршрутизатор и балансировщик нагрузки между подами.

Поды могут пересоздаваться, уничтожаться, переезжать на другие ноды и изменять IP-адреса. Если внешней системе или сервису будет нужно обратиться к поду, они должны быть в курсе его жизненного цикла и понимать, куда обращаться в конкретный момент времени. Это неудобно. Поэтому в Kubernetes есть сервисы, которые знают количество подов, хосты, на которых они работают, и пр. Сервис получает запрос от внешних систем или сервисов, определяет, какому именно поду его адресовать, и делает это.

## Компоненты кластера Kubernetes

<figure><img src="../../../../../../.gitbook/assets/osi (10).jpg" alt=""><figcaption><p>Компоненты на нодах</p></figcaption></figure>

1. **kube-apiserver.** С помощью сервера API обеспечивается работа API кластера, обрабатываются REST-операции и предоставляется интерфейс, через который остальные компоненты взаимодействуют друг с другом. Также через него проходят запросы на изменение состояния или чтение кластера.&#x20;
2. **kube-scheduler.** Компонент, планирующий, на каких узлах разворачивать поды. Он учитывает такие факторы, как ограничения, требования к ресурсам, местонахождение данных и пр.&#x20;
3. **etcd.** Распределенное хранилище в формате «ключ-значение». В нем хранится состояние всего кластера. Главная задача etcd — обеспечить отказоустойчивость кластера и консистентность данных. Etcd — самостоятельный проект. Он развивается отдельно от Kubernetes и применяется в разных продуктах.&#x20;
4. **kube-proxy.** Служба, которая управляет правилами балансировки нагрузки. Она конфигурирует правила IPVS или iptables, через которые выполняются проксирование и роутинг.&#x20;
5. **kube-controller-manager.** Компонент запускает работу контроллеров.
6. **kubelet.** Cлужба, которая управляет состоянием ноды: запуском, остановкой и поддержанием работы контейнеров и подов.

## Преимущества Kubernetes <a href="#preimushestva-i-nedostatki-kubernetes" id="preimushestva-i-nedostatki-kubernetes"></a>

#### Портативность и гибкость

Kubernetes не зависит от аппаратного обеспечения. Работающую платформу можно переносить на другой сервер, в частное или общедоступное облако. Главное требование — операционная система хоста должна иметь подходящую версию ОС Linux и Windows.

#### Экономичность

Крупным компаниям Kubernetes помогает уменьшить расходы на ИТ-инфраструктуру благодаря группировке приложений в пакеты. Это оптимизирует использование средств, инвестированных в инфраструктуру и оборудование. K8s дает много возможностей для масштабирования приложения и делает процесс более доступным. Одновременно он сокращает нагрузку на персонал, позволяет сотрудникам направить силы на решение других задач, повышает эффективность использования ресурсов инфраструктуры.

#### Поддержка мультиоблачности

Kubernetes позволяет работать с мультиоблачной средой, то есть выполнять рабочие задачи как в одном облаке, так и в нескольких. Также можно переносить систему из одной облачной среды в другую, повышая ее безопасность.

#### Эффективное распределение задач

Микросервисы Kubernetes эффективно распределяют задачи между рабочими группами. Это делает систему более гибкой и ускоряет выполнение большого объема работы. Разработчики контролируют большие приложения, включающие множество контейнеров, одновременно делая их более детализированными.

#### Наличие развитой экосистемы

Kubernetes поддерживает много крупных корпораций, но это свободное ПО. Фонд CNCF только контролирует его развитие, но не владеет им. Поэтому сторонние разработчики могут создавать дополнения, расширяющие функционал системы, обмениваться опытом друг с другом.&#x20;

#### Надежность

K8s уменьшает сложность облака, а также делает работу с ним более понятной и надежной. Это касается не только технических аспектов системы, но и вопросов безопасности информации, распределения прав доступа.







Исчтоники: [https://blog.skillfactory.ru/glossary/kubernetes/](https://blog.skillfactory.ru/glossary/kubernetes/)&#x20;