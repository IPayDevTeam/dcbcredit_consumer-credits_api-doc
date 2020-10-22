# Credits Payments

## Статусы кредита

```
new: По сути новый запрос на кредит
approved: Подтверждён
issued: Выданный кредит (активный)
overdue: Просрочен
returned: Возвращён
annul: Аннулирован
```


<br>


## Regular payment

### POST: `/consumer-credit/credit/:creditId/regular-payment?externalId=[ID]`

Запрос для оплаты **текущего** регулярного платежа по кредиту.

#### Route params:

| Param | Type | Description |
| ----- | ---- | ----------- |
| creditId | int | ID кредита из кредитной системы |

#### Query params:

| Param | Type | Description |
| ----- | ---- | ----------- |
| externalId | int | ID клиента из DCBanc |

?>ВАЖНО! Запрос без тела

#### Response:

```json
{
  "creditStatus": "issued|returned"
}
```


<br>


## Full return

### POST: `/consumer-credit/credit/:creditId/full-return?externalId=[ID]`

Запрос для полного врзврата **текущего** кредита.

#### Route params:

| Param | Type | Description |
| ----- | ---- | ----------- |
| creditId | int | ID кредита из кредитной системы |

#### Query params:

| Param | Type | Description |
| ----- | ---- | ----------- |
| externalId | int | ID клиента из DCBanc |

?>ВАЖНО! Запрос без тела

#### Response:

```json
{
  "creditStatus": "returned"
}
```
