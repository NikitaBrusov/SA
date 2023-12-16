# ✍ JSON + JSON Schema

{% hint style="info" %}
JSON (JavaScript Object Notation) — текстовый формат обмена данными, основанный на JavaScript.
{% endhint %}

## Ограничения и синтаксис JSON

Допустимые форматы данных для пары "key":"value" в JSON указаны в таблице ниже:

| Ключ "key" | Значение "value" |
| ---------- | ---------------- |
| string     | string           |
|            | number           |
|            | object           |
|            | array            |
|            | boolean          |
|            | null             |

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
                "Sciencejs": 80,
                "Compute": 66
            }
        }
        ],
    "name_school": "EKB Lyceum",
    "name_teacher": "LA"
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

<summary>Пример JSON Schema</summary>

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

### "Keywords" для описания схемы

<table data-full-width="true"><thead><tr><th width="176">Keywords</th><th width="183">Описание</th><th>Пример</th></tr></thead><tbody><tr><td><code>"$schema"</code></td><td>Используется для задания версии драфта схемы</td><td><p></p><pre><code>"$schema": http://json-schema.org/draft-04/schema#
</code></pre></td></tr><tr><td><code>"$id"</code></td><td>Используется для указания уникального идентификатора документа или его подсхем.</td><td><p></p><pre><code>"$id": "http://archi-blair.com/schemas/RolesDictionaryDef.json#"
</code></pre></td></tr><tr><td><code>"title" "description" "examples" "comment"</code></td><td>Комментарии к JSON схеме</td><td></td></tr></tbody></table>

### "Keywords" зависимые от типа данных

<table data-full-width="true"><thead><tr><th width="138">Тип данных</th><th width="184">Keywords</th><th width="240">Описание</th><th>Пример</th></tr></thead><tbody><tr><td><code>"type": "string"</code></td><td>minLength<br>maxLength</td><td>Длину строки можно ограничить с помощью ключевых слов <strong>minLength</strong> и <strong>maxLength</strong>. Для обоих ключевых слов значение должно быть неотрицательным числом.</td><td><pre><code>{
  "type": "string",
  "minLength": 2,
  "maxLength": 3
}
</code></pre></td></tr><tr><td></td><td>pattern</td><td>Формат строки можно огрничивать с помощью ключевого слова pattern. Паттерн задается с помощью регулярного выражения RegEx</td><td><pre><code>{
   "type": "string",
   "pattern": "^(\\([0-9]{3}\\))?[0-9]{3}-[0-9]{4}$"
}
</code></pre></td></tr><tr><td><code>"type": "number"</code></td><td>minimum<br>maximum<br>exclusiveMinimum<br>exclusiveMaximum </td><td><p>Диапазон числа можно ограничивать с помощью ключевых слов.</p><p>Если x - это проверяемое значение, то должно выполняться следующее:</p><ul><li>x ≥ minimum</li><li>x > exclusiveMinimum</li><li>x ≤ maximum</li><li>x &#x3C; exclusiveMaximum</li></ul></td><td><pre><code>{
  "type": "number",
  "minimum": 0,
  "exclusiveMaximum": 100
}
</code></pre></td></tr><tr><td></td><td>multipleOf</td><td>Кратность числа можно ограничивать с помощью multipleOf</td><td><pre><code>{
    "type": "number",
    "multipleOf" : 10
}
</code></pre></td></tr><tr><td><code>"type": "object"</code></td><td>properties</td><td>Тип данных объектов можно ограничивать с помощью properties</td><td><pre><code>{
  "type": "object",
  "properties": {
    "number": { "type": "number" },
    "street_name": { "type": "string" },
    "street_type": { "enum": ["Street", "Avenue", "Boulevard"] }
  }
}
</code></pre></td></tr><tr><td></td><td>patternProperties</td><td>Тип данных объектов можно ограничивать с помощью шаблонов свойств </td><td></td></tr><tr><td></td><td>additionalProperties </td><td></td><td></td></tr><tr><td></td><td>required</td><td>Ограничение  на  обязательные обьекты</td><td><pre><code> {
  "type": "object",
  "properties": {
    "name": { "type": "string" },
    "email": { "type": "string" },
    "address": { "type": "string" },
    "telephone": { "type": "string" }
  },
  "required": ["name", "email"]
}
</code></pre></td></tr><tr><td></td><td>propertyNames</td><td></td><td><pre><code>{
  "type": "object",
  "propertyNames": {
    "pattern": "^[A-Za-z_][A-Za-z0-9_]*$"
  }
}
</code></pre></td></tr><tr><td></td><td>minProperties<br>maxProperties</td><td>Количество свойств объекта можно ограничить с помощью ключевых слов</td><td><pre><code>{
  "type": "object",
  "minProperties": 2,
  "maxProperties": 3
}
</code></pre></td></tr><tr><td><code>"type": "array"</code></td><td>items </td><td>Ограничение на тип элементов массива (для всего массива)</td><td><pre><code>{
  "type": "array",
  "items": {
    "type": "number"
  }
}
</code></pre></td></tr><tr><td></td><td>prefixItems</td><td>Ограничение на тип элементов массива (для каждого конкретного индекса массива)</td><td><pre><code>{
  "type": "array",
  "prefixItems": [
    { "type": "number" },
    { "type": "string" },
    { "enum": ["Street", "Avenue", "Boulevard"] },
    { "enum": ["NW", "NE", "SW", "SE"] }
  ]
}
</code></pre></td></tr></tbody></table>







Источники:&#x20;

* [https://infostart.ru/1c/articles/1543922/](https://infostart.ru/1c/articles/1543922/)
* [https://infostart.ru/1c/articles/1546672/](https://infostart.ru/1c/articles/1546672/)
* Конвертер: [https://www.liquid-technologies.com/online-json-to-schema-converter](https://www.liquid-technologies.com/online-json-to-schema-converter)
