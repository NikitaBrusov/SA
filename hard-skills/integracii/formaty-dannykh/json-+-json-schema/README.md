# JSON + JSON Schema

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

<summary>Пример JSON</summary>

```json
{
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

### "Keywords", зависимые от типа данных
