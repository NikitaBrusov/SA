# JSON vs XML

<details>

<summary>Примеры JSON и XML</summary>

```json
JSON

{"Geeks":[ 
    { "firstName":"Vivek", "lastName":"Kothari" }, 
    { "firstName":"Suraj", "lastName":"Kumar" }, 
    { "firstName":"John", "lastName":"Smith" }, 
    { "firstName":"Peter", "lastName":"Gregory" } 
]}
```

```xml
XML

<Geeks> 
    <Geek> 
        <firstName>Vivek</firstName> <lastName>Kothari</lastName> 
    </Geek> 
    <Geek> 
        <firstName>Suraj</firstName> <lastName>Kumar</lastName> 
    </Geek> 
    <Geek> 
        <firstName>John</firstName> <lastName>Smith</lastName> 
    </Geek> 
    <Geek> 
        <firstName>Peter</firstName> <lastName>Gregory</lastName> 
    </Geek> 
</Geeks>
```

</details>

| JSON                                             | XML                                                                                                                          |
| ------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------- |
| Это просто формат, написанный на JavaScript      | Это язык разметки, который использует структуру тегов для представления элементов данных                                     |
| Данные хранятся как карта с парами ключ-значение | Данные XML хранятся в виде древовидной структуры                                                                             |
| Не использует закрывающий тег                    | Имеет начальный и конечный теги                                                                                              |
| Имеет меньший размер файлов                      | Имеет больший размер файлов                                                                                                  |
| Файлы очень легко читать по сравнению с XML      | Файлы трудно читать и интерпретировать                                                                                       |
| Менее защищен                                    | Более безопасен, чем JSON                                                                                                    |
| Не поддерживает комментарии                      | <p>Поддерживает комментарии<br>&#x3C; !--Your comment-- ></p>                                                                |
| Поддерживает массив                              | Не поддерживает массивы напрямую. Чтобы иметь возможность использовать массив, необходимо добавить теги для каждого элемента |







Источники:&#x20;

* [https://hackr.io/blog/json-vs-xml](https://hackr.io/blog/json-vs-xml)
* [https://www.geeksforgeeks.org/difference-between-json-and-xml/](https://www.geeksforgeeks.org/difference-between-json-and-xml/)
