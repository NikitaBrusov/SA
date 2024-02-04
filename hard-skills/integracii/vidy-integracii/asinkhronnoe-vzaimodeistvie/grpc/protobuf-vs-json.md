# Protobuf vs JSON

| Критерий                | Protocol Buffers (ProtoBuf)                                           | JSON                                                |
| ----------------------- | --------------------------------------------------------------------- | --------------------------------------------------- |
| **Формат данных**       | Бинарный                                                              | Текстовый                                           |
| **Размер сообщений**    | Обычно меньше, более компактные                                       | Обычно больше из-за текстового формата              |
| **Скорость обработки**  | Быстрее из-за меньшего размера и бинарной природы                     | Медленнее, требует парсинга текста                  |
| **Читаемость**          | Требует специальных инструментов для чтения и отладки                 | Легко читаем и отлаживаем человеком                 |
| **Интероперабельность** | Хорошая поддержка между различными япами                              | Отличная поддержка на всех платформах               |
| **Совместимость**       | Строгая совместимость, требует точного соответствия схемы данных      | Гибкая, легко адаптируется к изменениям             |
| **Типизация данных**    | Строго типизированный, требует определения всех полей                 | Динамически типизированный                          |
| **Использование**       | Предпочтительнее для высокопроизводительных и оптимизированных систем | Широко используется для веб-API и легкой интеграции |







Источник: [https://habr.com/ru/companies/otus/articles/780720/](https://habr.com/ru/companies/otus/articles/780720/)