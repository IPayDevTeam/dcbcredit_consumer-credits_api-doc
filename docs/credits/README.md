# Credits General


<br>


## Submission

### POST `/consumer-credit/submit`

Подача заявки на кредит.

#### Route params:

| Param | Type | Description |
| --------- | ---- | ----------- |
| externalId | int | ID юзера из системы **DCBanc** |

#### Request:

(Тут подаются все те-же поля что и в [`POST:/consumer-credit/calculator`](/calculator?id=calculation ':target=_blank'), а так-же `order_id`, и инфа о юзере).

```json
{
    "order_id": "112233", // Информативный ID ордера
    "currency": "eur",
    "term": 4, // Срок в месяцах
    "first_installment_percent": 15,
    "purchase_amount": 1000, // Сумма которая предоставлена в кредит
    "name": "Vasja",
    "surname": "Pupkin",
    "email": "examle@example.com",
    "phone": "123456789",
    "lang": "en" // Язык юзера (Лучше оставить как есть пока)
    "email_verified": 1 (Boolean = 1|0, наверное всегда будет 1)
    "phone_verified": 1 (Boolean = 1|0, наверное всегда будет 1)
    "items": [ // Список товаров и которые оформляются в кредит и минимальные данные продавцов (ID и WalletID из DCBanc)
        {
            "title": "product 1", // Для информации название товара
            "externalId": "24046", // ID продавца
            "walletId": "246402", // ID кошелька продавца из DCBanc
            "purchaseAmount": 200 // Стоимость товара (общая сумма всех товаров должна совпадать с `purchase_amount`)
        },
        {
            "title": "product 2",
            "externalId": "24046",
            "walletId": "246402",
            "purchaseAmount": 300
        },
        {
            "title": "product 3",
            "externalId": "24046",
            "walletId": "246402",
            "purchaseAmount": 500
        }
    ]
}
```

#### Response:

```json
{
    "data": {
        "credit_id": 777 // ID созданного ID в системе кредитов
    }
}
```


<br>


## List of credits

### GET `/consumer-credit/credits?externalId=[id]&type=[active|closed]`

Возвращает список всех кредитов клиента отфильрованных по статусу, список имеет паджинацию.

#### Query params:

| Param | Type | Description |
| ----- | ---- | ----------- |
| externalId | int | ID клиента из системы DCBanc |
| type `optional` | string | В каком статусе вернуть список `active` или `closed`. *(По умолчанию `active`)* |

#### Response:

Возвращает коллекцию обьектов кредита.

Информация об обьекте кредита: [Credit](objects?id=credit ':target=_blank')

```json
{
    "data": [
        {
            "id": "23",
            "origin_id": "3",
            "currency": "eur",
            "client_id": "86166",
            "order_id": "112235",
            "external_id": "25600",
            "consumer_credit_setting_id": "1",
            "status": "new",
            "purchase_amount": "1000.00",
            "term": "4",
            "first_installment_amount": "150.00",
            "issue_commission_amount": "0.00",
            "issued_at": null,
            "contract_accepted_at": null,
            "contract_code": "g484413",
            "created_at": "2020-09-24 06:59:43",
            "created_by": null,
            "updated_at": null,
            "updated_by": null,
            "deleted_at": null,
            "deleted_by": null,
            "origin": {
                "id": "3",
                "domain": "localhost:8080"
            }
        },
        ...
    ],
    "links": {
        "self": {
            "href": "http://apiUrl.local/consumer-credit/credits?externalId=25600&type=active&page=1"
        }
    },
    "meta": {
        "totalCount": 2,
        "pageCount": 1,
        "currentPage": 1,
        "perPage": 20
    }
}
```


<br>


##  Credit data

### GET `/consumer-credit/credits/:creditId?externalId=[id]`

Врзвращает данные по однопу кредиту по его **ID**.

#### Route params:

| Param | Type | Description |
| --------- | ---- | ----------- |
| creditId | int | ID кредита из кредитной системы |

#### Query params:

| Param | Type | Description |
| ----- | ---- | ----------- |
| externalId | int | ID клиента из системы DCBanc |

#### Response:

Возвращает обьект кредита.

Информация об обьекте кредита: [Credit](objects?id=credit ':target=_blank')

```json
{
    "data": {
        "id": "23",
        "origin_id": "3",
        "currency": "eur",
        "client_id": "86166",
        "order_id": "112235",
        "external_id": "25600",
        "consumer_credit_setting_id": "1",
        "status": "new",
        "purchase_amount": "1000.00",
        "term": "4",
        "first_installment_amount": "150.00",
        "issue_commission_amount": "0.00",
        "issued_at": null,
        "contract_accepted_at": null,
        "contract_code": "g484413",
        "created_at": "2020-09-24 06:59:43",
        "created_by": null,
        "updated_at": null,
        "updated_by": null,
        "deleted_at": null,
        "deleted_by": null,
        "origin": {
            "id": "3",
            "domain": "localhost:8080"
        }
    }
}
```


<br>


## Credit amounts

### GET `/consumer-credit/credits/:creditId/amounts?externalId=[id]`

Возвращает информацию о суммах и платежах по кредиту.

#### Route params:

| Param | Type | Description |
| --------- | ---- | ----------- |
| creditId | int | ID кредита из кредитной системы |

#### Query params:

| Param | Type | Description |
| ----- | ---- | ----------- |
| externalId | int | ID клиента из системы DCBanc |

#### Response:

?> Todo
