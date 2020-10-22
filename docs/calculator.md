# Calculator


<br>


## Meta data

### GET `/consumer-credit/calculator`

Получение информации для калькулятора (или слайдера). Исключительно информативные данные не относящиеся к конкретному товару.

#### Query params:

| Param | Type | Description |
| --------- | ---- | ----------- |
| currency | string | Валюта в какой оформлять кредит (для разных валют есть разные настройи и разные процентные ставки) |

#### Response:

```json
{
    "data": {
        "currency": "eur",
        "percent_per_month": 0.5, // Процент кредита в месяц
        "term_min_months": 1,
        "term_max_months": 24,
        "min_first_installment_percent": 5,
        "max_first_installment_percent": 50,
        "first_installment_percent_step": 5, // Шаг первого взноса для слайдера или калькулятора
        "max_purchase_amount": "1000.00" // Максимальная сумма товара который можно взять в кредит на данной валюте и в данный период времени (Что-то типа текущих настроек по валюте)
    }
}
```


<br>


## Calculation

### POST `/consumer-credit/calculator`

Получение данных по кредит для определённой суммы (на товар).

#### Request:

```json
{
    "currency": "usd",
    "term": 3, // Срок в месяцах
    "first_installment_percent": 50, // Процент первого взноса (может быть от минимального до максимального. Эти цифры берём из метода `GET:/consumer-credit/calculator`)
    "purchase_amount": 1000 // Сумма товара как она есть
}
```

#### Response:

```json
{
    "data": {
        "currency": "eur",
        "paymentAmount": 168.34, // Подсчитанный ежемесячный платёж с учётом первого взноса
        ...
        "purchaseAmount": 500, // Сумма которую предоставляем в кредит (тоесть сумма покупки минус сумма первого взноса)
        ...
        "amountAvailableOnCredit": 950 // Сумма которую можем предоставить в кредит по определённой сумме товара (сумма товара - сумма минимально первого взноса. Если первого взноса по настройкам может не быть, то тут будет вся стоимость товара)
    }
}
```


<br>


## Calculate schedule

### POST `/consumer-credit/calculator/schedule`

Калькулирует заявку и возвращает полный график платежей со всеми данными

#### Request:

```json
{
  "currency": "usd",
  "term": 4,
  "first_installment_percent": 10,
  "purchase_amount": 1000
}
```

#### Response:

?> TODO
