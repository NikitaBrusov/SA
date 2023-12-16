---
description: реальная модель
---

# TCP/IP

<figure><img src="../../../.gitbook/assets/osi (2).jpg" alt=""><figcaption><p>TCP/IP</p></figcaption></figure>

**Модель TCP/IP** (Transmission Control Protocol/Internet Protocol) — это сетевая модель, которая описывает принципы передачи данных в компьютерных сетях. Она является основой для организации и взаимодействия сетей в Интернете.

Модель TCP/IP состоит из четырех основных уровней:

1. **Канальный уровень (Network Access Layer):** Этот уровень определяет методы физической передачи данных через среды связи, такие как Ethernet или Wi-Fi, а также протоколы для управления доступом к среде передачи, такие как Ethernet MAC или Wi-Fi MAC. Он обеспечивает непосредственное подключение устройств к физическим средам передачи данных.
2. **Сетевой уровень (Internet Layer):** На этом уровне выполняется маршрутизация пакетов данных в компьютерной сети. Он использует IP (Internet Protocol) для адресации узлов в сети и определяет протоколы, такие как ICMP (Internet Control Message Protocol) для обмена сообщениями об ошибках и настройках сети.
3. **Транспортный уровень (Transport Layer):** Этот уровень обеспечивает надежную доставку данных от отправителя к получателю. Он использует протоколы TCP (Transmission Control Protocol) и UDP (User Datagram Protocol). TCP обеспечивает гарантированную доставку данных с контролем потока и обнаружением ошибок, в то время как UDP обеспечивает безгарантийную доставку без контроля потока.
4. **Прикладной уровень (Application Layer):** На этом уровне находятся приложения и службы, работающие поверх TCP/IP. Они включают протоколы и службы, такие как HTTP (передача гипертекста), FTP (передача файлов), SMTP (почтовый протокол), DNS (система доменных имен) и многие другие.







Источник: [https://testengineer.ru/modeli-osi-iso-i-tcp-ip/](https://testengineer.ru/modeli-osi-iso-i-tcp-ip/)
