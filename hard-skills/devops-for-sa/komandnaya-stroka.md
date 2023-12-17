# Командная строка

{% hint style="info" %}
**Командная строка** — текстовый интерфейс пользователя для взаимодействия с операционной системой компьютера и/или другим программным обеспечением с помощью команд, вводимых с клавиатуры. С его помощью пользователь может запускать и отключать другие программы, системные процессы, редактировать реестр, управлять файлами и папками, а также программировать с использованием встроенного скриптового языка.
{% endhint %}

{% hint style="info" %}
**Bash (Bourne again shell)** — это стандартная командная оболочка в большинстве дистрибутивов Linux и macOS, а также язык для этой оболочки.
{% endhint %}

{% hint style="info" %}
**cmd** — это стандартная командная оболочка в операционных системах Windows.
{% endhint %}

## bash vs cmd

<table data-full-width="false"><thead><tr><th width="185">bash</th><th width="147">cmd</th><th>Описание команды </th></tr></thead><tbody><tr><td>ls -l <br>(флаг l показывает скрытые файлы)</td><td>dir</td><td>показывает содержимое директории</td></tr><tr><td>pwd</td><td>cd</td><td>показывает путь к текущей директории</td></tr><tr><td>touch</td><td>echo</td><td>создает новый файл</td></tr><tr><td>mkdir</td><td>md или mkdir</td><td>создает новый каталог</td></tr><tr><td>rm</td><td>del</td><td>удаляет файл</td></tr><tr><td>rm -r</td><td>rmdir</td><td>удаляет каталог</td></tr><tr><td>cat</td><td>type</td><td>отображает содержимое файла</td></tr><tr><td>rename</td><td>ren</td><td>переименовывает файл</td></tr><tr><td>mv</td><td>move</td><td>перемещает файл</td></tr><tr><td>cp</td><td>xcopy</td><td>копирует файл или папку</td></tr><tr><td>grep _</td><td>findstr _</td><td>поиск строки в результатах команды</td></tr><tr><td>grep _1 _2</td><td>find _2 _1</td><td>поиск строки 1 в файлах 2</td></tr><tr><td>find -name _</td><td>dir _ -s</td><td>поиск файла</td></tr><tr><td>chmod</td><td>icacls</td><td>изменение прав доступа</td></tr><tr><td>chown __ _</td><td>takeown -f _</td><td>изменить владельца</td></tr><tr><td>du _ -hs</td><td>dir _</td><td>узнать размер директории</td></tr><tr><td>sudo</td><td>runas</td><td>выполняет команды в текущей оболочке от имени администратора</td></tr></tbody></table>







Источники:

* [https://blog.skillfactory.ru/glossary/komandnaya-stroka/](https://blog.skillfactory.ru/glossary/komandnaya-stroka/)
* [https://coding-style.ru/blog/article-7](https://coding-style.ru/blog/article-7)
* [https://serverspace.ru/support/help/shpargalka-po-cmd-komandam-v-windows/](https://serverspace.ru/support/help/shpargalka-po-cmd-komandam-v-windows/)
* [https://timeweb.com/ru/community/articles/komandnaya-stroka-ubuntu-osnovnye-komandy-bash-1](https://timeweb.com/ru/community/articles/komandnaya-stroka-ubuntu-osnovnye-komandy-bash-1)
