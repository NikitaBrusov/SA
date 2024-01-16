# Page 1

<table data-full-width="true"><thead><tr><th width="138">Тип данных</th><th width="184">Keywords</th><th width="240">Описание</th><th>Пример</th></tr></thead><tbody><tr><td><code>"type": "string"</code></td><td>minLength<br>maxLength</td><td>Длину строки string можно ограничить с помощью ключевых слов <strong>minLength</strong> и <strong>maxLength</strong>. Для обоих ключевых слов значение должно быть неотрицательным числом.</td><td><pre><code>{
  "type": "string",
  "minLength": 2,
  "maxLength": 3
}
</code></pre></td></tr><tr><td></td><td>pattern</td><td>Формат строки string можно огрничивать с помощью ключевого слова pattern. Паттерн задается с помощью регулярного выражения RegEx</td><td><pre><code>{
   "type": "string",
   "pattern": "^(\\([0-9]{3}\\))?[0-9]{3}-[0-9]{4}$"
}
</code></pre></td></tr><tr><td><code>"type": "number"</code></td><td>minimum<br>maximum<br>exclusiveMinimum<br>exclusiveMaximum </td><td><p>Диапазон числа number можно ограничивать с помощью ключевых слов.</p><p>Если x - это проверяемое значение, то должно выполняться следующее:</p><ul><li>x ≥ minimum</li><li>x > exclusiveMinimum</li><li>x ≤ maximum</li><li>x &#x3C; exclusiveMaximum</li></ul></td><td><pre><code>{
  "type": "number",
  "minimum": 0,
  "exclusiveMaximum": 100
}
</code></pre></td></tr><tr><td></td><td>multipleOf</td><td>Кратность числа number можно ограничивать с помощью multipleOf</td><td><pre><code>{
    "type": "number",
    "multipleOf" : 10
}
</code></pre></td></tr><tr><td><code>"type": "object"</code></td><td>properties</td><td>Тип данных объектов object можно ограничивать с помощью properties в котором прописаны ограничения для каждого объекта</td><td><pre><code>{
  "type": "object",
  "properties": {
    "number": { "type": "number" },
    "street_name": { "type": "string" },
    "street_type": { "enum": ["Street", "Avenue", "Boulevard"] }
  }
}
</code></pre></td></tr><tr><td></td><td>patternProperties</td><td>Тип данных объектов object можно ограничивать с помощью шаблонов свойств </td><td></td></tr><tr><td></td><td>additionalProperties </td><td>Используется для управления обработкой дополнительных элементов, не входящих ни в properties, ни в patternProperties</td><td></td></tr><tr><td></td><td>required</td><td>Ограничение  на  обязательные обьекты</td><td><pre><code> {
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
