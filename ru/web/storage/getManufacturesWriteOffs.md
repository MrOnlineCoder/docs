## storage.getManufacturesWriteOffs: Списания по производствам

> Пример запроса:

```php
<?php
$url = 'https://joinposter.com/api/storage.getManufacturesWriteOffs'
 . '?token=687409:4164553abf6a031302898da7800b59fb'
 . '&date_from=2017-11-30'
 . '&date_to=2017-11-30'
 . '&per_page=10'
 . '&page=5';

$data = sendRequest($url);
```

> Пример ответа:

```json
{  
  "response":{  
    "count":11,
    "page":{  
      "per_page":10,
      "page":2,
      "count":1
    },
    "data":[  
      {  
        "manufacture_id":15,
        "storage_id":2,
        "date":"2017-11-30 15:00:00",
        "products":[  
          {  
            "product_id":105,
            "type":2,
            "num":10,
            "sum":123.45,
            "sum_netto":102.88,
            "is_fiscal":0,
            "write_offs":[  
              {  
                "ingredient_id":165,
                "type":1,
                "weight":123.45
              }
            ]
          }
        ]
      }
    ]
  }
}
```

Метод возвращает списания по производствам в диапазоне дат и с постраничной разбивкой

### HTTP GET запрос

`https://joinposter.com/api/storage.getManufacturesWriteOffs`

### GET-параметры запроса storage.getManufacturesWriteOffs

Параметр | Описание
-------- | --------
date_from | Дата начала выборки, формат "Y-m-d"
date_to | Дата конца выборки, формат "Y-m-d"
per_page | Количество чеков на одной странице. По умолчанию принимает 100, максимальное значение — 1000.
page | Номер страницы, по умолчанию принимает 1

### Параметры ответа storage.getManufacturesWriteOffs

Внутри параметра `response` лежит объект, внутри которого есть следующие параметры:

Параметр | Описание
-------- | --------
count | Общее количество чеков в выбранном диапазоне дат
page | Информация о странице
data | Информация по чекам

Внутри параметра `page` лежит объект, внутри которого есть следующие параметры:

Параметр | Описание
-------- | --------
per_page | Количество чеков на одной странице
page | Номер текущей страницы
count | Количество чеков на текущей странице 

Внутри параметра `data` лежит массив, в каждом элементе которого есть следующие параметры:

Параметр | Описание
-------- | --------
manufacture_id | Id производства
storage_id | Id склада
date | Дата производства
products | Произведённые полуфабрикаты и тех. карты

Внутри параметра `products` лежит массив, в каждом элементе которого есть следующие параметры:

Параметр | Описание
-------- | --------
product_id | Id полуфабриката или тех. карты
type | Тип: 1 — полуфабрикат, 2 — тех. карта
num | Количество
sum | Общая стоимость за всё количество
sum_netto | Общая стоимость без НДС за всё количество. Возвращается если включена настройка «Считать себестоимость и прибыль нетто»
is_fiscal | Признак фискальности: 0 — не фискальный, 1 — фискальный
write_offs | Список списаний

Внутри параметра `write_offs` лежит массив, в каждом элементе которого есть следующие параметры:

Параметр | Описание
-------- | --------
ingredient_id | Id ингредиента
type | Тип: 1 — ингредиент, 2 — полуфабрикат
weight | Общее количество