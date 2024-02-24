---
description: XML Schema
---

# XSD

{% hint style="info" %}
**XSD (Xml Schema Definition)** — это язык описания структуры XML документа. Его также называют XML Schema. При использовании XML Schema XML парсер может проверить не только правильность синтаксиса XML документа, но также его структуру, модель содержания и типы данных.
{% endhint %}

Такой подход позволяет объектно-ориентированным языкам программирования легко создавать объекты в памяти, что, несомненно, удобнее, чем разбирать XML как обычный текстовый файл.

## Структура

Документ XSD начинается с корневого элемента `schema`. Каждый тег в XML-документе определяется с помощью тега `element`. Каждый из этих элементов может содержать простое содержимое (например, строку или дату) или более сложные данные (например, вложенные элементы).

**Например:** вы пишете XSD для XML-документа, описывающего клиента. В XSD вы можете объявить, что у Клиента должен быть 1 адрес и что каждый адрес должен содержать состояние, но почтовый индекс не является обязательным:

<details>

<summary>Простой пример XML</summary>

```xml
<Customer>
  <Name>Bob Carolgees</Name>
  <Address>
    <Street>1 Homer Street</Street>
    <City>Flanville</City>
    <State>BZ</State>
    <Country>DE</Country>
  </Address>
</Customer>
```

</details>

<details>

<summary>Простой пример XSD</summary>

```xml
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">

  <xsd:element name="Customer" type="CustomerType"/>

  <xsd:complexType name="CustomerType">
    <xsd:sequence>
      <xsd:element name="Name" type="xsd:string"/>
      <xsd:element name="Address" type="AddressType"/>
    </xsd:sequence>
  </xsd:complexType>

  <xsd:complexType name="AddressType">
    <xsd:sequence>
      <xsd:element name="Street" type="xsd:string"/>
      <xsd:element name="City" type="xsd:string"/>
      <xsd:element name="State" type="xsd:string"/>
      <xsd:element name="ZipCode" type="xsd:string" minOccurs="0"/>
      <xsd:element name="Country" type="xsd:string"/>
    </xsd:sequence>
  </xsd:complexType>

</xsd:schema>
```

</details>







Источники:

* [https://habr.com/ru/articles/90696/](https://habr.com/ru/articles/90696/)
* [https://www.tutorialworks.com/xsd-vs-wsdl/](https://www.tutorialworks.com/xsd-vs-wsdl/)
