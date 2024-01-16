# JSON + JSON Schema

{% hint style="info" %}
JSON (JavaScript Object Notation) — текстовый формат обмена данными, основанный на JavaScript.
{% endhint %}

## Ограничения и синтаксис JSON

Допустимые форматы данных для пары "key":"value" в JSON указаны в карточках ниже:

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td><strong>Ключ "key"</strong></td><td>string</td><td></td></tr><tr><td><strong>Значение "value"</strong></td><td>string<br>number (integer)<br>object<br>array<br>boolean<br>null</td><td></td></tr></tbody></table>

Основные правила синтаксиса:

1. Данные записываются в виде пар {“ключ”: значение}.
2. Данные разделяются запятыми.
3. В фигурных скобках записываются объекты.
4. В квадратных скобках записываются массивы.
5. Наименования «ключей» регистрозависимы.

<details>

<summary>Пример JSON</summary>

```json
{
    "students": [
        {
            "id": 101,
            "name": "Max",
            "score": {
                "Math": 90,
                "Science": 80,
                "Compute": 70
            }
        },
        {
            "id": 102,
            "name": "Sam",
            "score": {
                "Math": 76,
                "Science": 80,
                "Compute": 66
            }
        }
        ],
    "name_school": "EKB Lyceum",
    "name_teacher": "TO"
}
```

</details>

## JSON Schema

{% hint style="info" %}
JSON Schema – это своеобразный язык описания структуры JSON-документации. Базируется на разных концепциях. Выступает в качестве самоописательного языка.
{% endhint %}

Схема создана для описания JSON-данных, но и сама она при этом является JSON-объектом. С помощью ключевых слов (keywords) в схеме создаются правила валидации структуры объекта и типов его полей.

<details>

<summary>Простой пример JSON</summary>

```json
{
  "id": 210700286,
  "first_name": "Lindsey",
  "last_name": "Stirling"
}
```

</details>

<details>

<summary>Пример простой JSON Schema</summary>

```json
{
      "type": "object",
      "properties": {
        "id": {
          "type": "integer",
          "description": "User ID"
        },
        "first_name": {
          "type": "string",
          "description": "User first name"
        },
        "last_name": {
          "type": "string",
          "description": "User last name"
        }
      },
      "required": [
        "id",
        "first_name",
        "last_name"
      ]
}
```

</details>

## "Keywords" для описания схемы

<table data-full-width="true"><thead><tr><th width="176">Keywords</th><th width="183">Описание</th><th>Пример</th></tr></thead><tbody><tr><td><code>"$schema"</code></td><td>Используется для задания версии драфта схемы</td><td><p></p><pre><code>"$schema": http://json-schema.org/draft-04/schema#
</code></pre></td></tr><tr><td><code>"$id"</code></td><td>Используется для указания уникального идентификатора документа или его подсхем.</td><td><p></p><pre><code>"$id": "http://archi-blair.com/schemas/RolesDictionaryDef.json#"
</code></pre></td></tr><tr><td><code>"title" "description" "examples" "comment"</code></td><td>Комментарии к JSON схеме</td><td></td></tr></tbody></table>

## "Keywords" зависимые от типа данных

### `Тип данных: "type": "string"`

<table data-full-width="true"><thead><tr><th width="136">Keywords</th><th width="240">Описание</th><th width="342">Пример JSON Shema</th><th>Примеры JSON сообщения</th></tr></thead><tbody><tr><td>minLength<br>maxLength</td><td>Длину строки string можно ограничить с помощью ключевых слов <strong>minLength</strong> и <strong>maxLength</strong>. Для обоих ключевых слов значение должно быть неотрицательным числом.</td><td><pre><code>{
  "type": "string",
  "minLength": 2,
  "maxLength": 3
}
</code></pre></td><td><pre><code>// Положительный кейс 
{ "АB" } или { "АBС" }

// Отрицательный кейс
{ "АBCD" } 
</code></pre></td></tr><tr><td>pattern</td><td>Формат строки string можно ограничивать с помощью ключевого слова pattern. Паттерн задается с помощью регулярного выражения RegEx</td><td><pre><code>{
   "type": "string",
   "pattern": "^(\\([0-9]{3}\\))?[0-9]{3}-[0-9]{4}$"
}
</code></pre></td><td><pre><code>// Положительный кейс 
{ "555-1212" }

// Отрицательный кейс
{ "(800)FLOWERS" } 
</code></pre></td></tr></tbody></table>

### `Тип данных: "type": "number"`

<table data-full-width="true"><thead><tr><th width="192">Keywords</th><th width="240">Описание</th><th>Пример JSON Shema</th><th>Примеры JSON сообщения</th></tr></thead><tbody><tr><td>minimum<br>maximum<br>exclusiveMinimum<br>exclusiveMaximum </td><td><p>Диапазон числа number можно ограничивать с помощью ключевых слов.</p><p>Если x - это проверяемое значение, то должно выполняться следующее:</p><ul><li>x ≥ minimum</li><li>x > exclusiveMinimum</li><li>x ≤ maximum</li><li>x &#x3C; exclusiveMaximum</li></ul></td><td><pre><code>{
  "type": "number",
  "minimum": 0,
  "exclusiveMaximum": 100
}
</code></pre></td><td><pre><code>// Положительный кейс 
{ 0 } или { 99 } или { 10 }

// Отрицательный кейс
{ 100 } или { -1 }
</code></pre></td></tr><tr><td>multipleOf</td><td>Кратность числа number можно ограничивать с помощью multipleOf</td><td><pre><code>{
    "type": "number",
    "multipleOf" : 10
}
</code></pre></td><td><pre><code>// Положительный кейс 
{ 10 } или { 20 }

// Отрицательный кейс
{ 23 }
</code></pre></td></tr></tbody></table>

### `Тип данных: "type": "object"`

<table data-full-width="true"><thead><tr><th width="130">Keywords</th><th width="204">Описание</th><th width="341">Пример JSON Shema</th><th>Примеры JSON сообщения</th></tr></thead><tbody><tr><td>properties</td><td>Тип данных объектов object можно ограничивать с помощью properties в котором прописаны ограничения для каждого объекта</td><td><pre><code>{
  "type": "object",
  "properties": {
    "number": { "type": "number" },
    "street_name": { "type": "string" },
    "street_type": { "enum": ["Street", "Avenue", "Boulevard"] }
  }
}
</code></pre></td><td><pre><code>// Положительный кейс 
{ "number": 1600, "street_name": "Pennsylvania", "street_type": "Avenue" }

// Отрицательный кейс
{ "number": "1600", "street_name": "Pennsylvania", "street_type": "Avenue" }
</code></pre></td></tr><tr><td>patternProperties</td><td>Тип данных объектов object можно ограничивать с помощью шаблонов свойств </td><td><pre><code>{
  "type": "object",
  "patternProperties": {
    "^S_": { "type": "string" },
    "^I_": { "type": "integer" }
  }
}
</code></pre></td><td><pre><code>// Положительный кейс 
{ "S_25": "This is a string" }
{ "I_0": 42 }

// Отрицательный кейс
{ "S_0": 42 }
</code></pre></td></tr><tr><td>additionalProperties </td><td>Используется для управления обработкой дополнительных элементов, не входящих ни в properties, ни в patternProperties</td><td><pre><code>{
  "type": "object",
  "properties": {
    "number": { "type": "number" },
    "street_name": { "type": "string" },
    "street_type": { "enum": ["Street", "Avenue", "Boulevard"] }
  },
  "additionalProperties": false
}
</code></pre></td><td><pre><code>// Положительный кейс 
{ "number": 1600, "street_name": "Pennsylvania", "street_type": "Avenue" }

// Отрицательный кейс
{ "number": 1600, "street_name": "Pennsylvania", "street_type": "Avenue", "direction": "NW" }
</code></pre></td></tr><tr><td>required</td><td>Ограничение  на  обязательные объекты object</td><td><pre><code> {
  "type": "object",
  "properties": {
    "name": { "type": "string" },
    "email": { "type": "string" },
    "address": { "type": "string" },
    "telephone": { "type": "string" }
  },
  "required": ["name", "email"]
}
</code></pre></td><td><pre><code>// Положительный кейс 
{ 
  "name": "William",
  "email": "bill@stratford.co.uk",
  "address": "Henley Street,England",
  "telephone": "1234"
}

// Отрицательный кейс
{
  "name": "William",
  "address": "Henley Street,England"
}
</code></pre></td></tr><tr><td>propertyNames</td><td>Формат элементов объекта object можно ограничивать с помощью ключевого слова propertyNames. Паттерн задается с помощью регулярного выражения RegEx</td><td><pre><code>{
  "type": "object",
  "propertyNames": {
    "pattern": "^[A-Za-z_][A-Za-z0-9_]*$"
  }
}
</code></pre></td><td><pre><code>// Положительный кейс 
{ "_a_proper_token_001": "value" }

// Отрицательный кейс
{ "001 invalid": "value" }
</code></pre></td></tr><tr><td>minProperties<br>maxProperties</td><td>Количество свойств объекта можно ограничить с помощью ключевых слов</td><td><pre><code>{
  "type": "object",
  "minProperties": 2,
  "maxProperties": 3
}
</code></pre></td><td><pre><code>// Положительный кейс 
{ "a": 0, "b": 1 }

// Отрицательный кейс
{ "a": 0 }
</code></pre></td></tr></tbody></table>

### `Тип данных: "type": "array"`

<table data-full-width="true"><thead><tr><th width="184">Keywords</th><th width="240">Описание</th><th>Пример JSON Shema</th><th>Примеры JSON сообщения</th></tr></thead><tbody><tr><td>items </td><td>Ограничение на тип элементов массива (для всего массива)</td><td><pre><code>{
  "type": "array",
  "items": {
    "type": "number"
  }
}
</code></pre></td><td><pre><code>// Положительный кейс 
[1, 2, 3, 4, 5]

// Отрицательный кейс
[1, 2, "3", 4, 5]
</code></pre></td></tr><tr><td>prefixItems</td><td>Ограничение на тип элементов массива (для каждого конкретного индекса массива)</td><td><pre><code>{
  "type": "array",
  "prefixItems": [
    { "type": "number" },
    { "type": "string" },
    { "enum": ["Street", "Avenue", "Boulevard"] },
    { "enum": ["NW", "NE", "SW", "SE"] }
  ]
}
</code></pre></td><td><pre><code>// Положительный кейс 
[1600, "Pennsylvania", "Avenue", "NW"]

// Отрицательный кейс
[1600, "Pennsylvania", "Avenue", "MOSCOW"]
</code></pre></td></tr><tr><td>contains</td><td>Ограничение на содержание элемента в массиве</td><td><pre><code>{
   "type": "array",
   "contains": {
     "type": "number"
   }
}
</code></pre></td><td><pre><code>// Положительный кейс 
["life", "universe", "everything", 42]

// Отрицательный кейс
["life", "universe", "everything", "forty-two"]
</code></pre></td></tr><tr><td>minItems<br>maxItems</td><td>Ограничение на длину массива </td><td><pre><code>{
  "type": "array",
  "minItems": 2,
  "maxItems": 3
}
</code></pre></td><td><pre><code>// Положительный кейс 
[1, 2]

// Отрицательный кейс
[1, 2, 3, 4]
</code></pre></td></tr></tbody></table>







Источники:&#x20;

* [https://infostart.ru/1c/articles/1543922/](https://infostart.ru/1c/articles/1543922/)
* Подробнее про JSON Shema: [https://infostart.ru/1c/articles/1546672/](https://infostart.ru/1c/articles/1546672/)
* Конвертер: [https://www.liquid-technologies.com/online-json-to-schema-converter](https://www.liquid-technologies.com/online-json-to-schema-converter)
