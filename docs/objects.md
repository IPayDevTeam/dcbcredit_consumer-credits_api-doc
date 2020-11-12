# Objects


<br>


## Amortization Payment

Обьект который возвращается во время калькуляций

#### Params:

?> Todo


<br>


## Credit

Обьект кредита, возвращается в списке или в выборке опеределённого кредита

#### Params:

| Param | Type | Description |
| ----- | ---- | ----------- |
| id | string | ID Обьекта |
| origin_id | string | ID Ориджина |
| currency | string | Валюта кредита |
| client_id | string | ID Клиента |
| order_id | string | ID Ордера |
| external_id | string | ID Клиента из DCBanc |
| consumer_credit_setting_id | string | ID Настроек по кредиту *(Каждая валюта имеет свои собственные настройки)* |
| status | string | Статус |
| purchase_amount | string | Запрашиваемая сумма кредита |
| term | string | Срок в месяцах |
| first_installment_amount | string | Сумма первого взноса |
| issue_commission_amount | string | Комиссия за выдачу кредита |
| issued_at | string | Дата выдачи кредита |
