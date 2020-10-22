# Clients


<br>


## Get client data

### GET `/consumer-credit/client/:clientId`

Возвращает данные клиента по **ID** или **ExternalID**.

#### Route params:

| Param | Type | Description |
| ----- | ---- | ----------- |
| clientId | int | ID юзера из кредитов или из DCBanc |

#### Query params:

| Param | Type | Description |
| ----- | ---- | ----------- |
| byExternalId `optional` | `0` или `1` | Выборка по ID из DCBanc или внутренней системы кредитов |

#### Response:

```json
"data":  {
  "id":  86162,
  "personal_code":  "010203",
  "name":  "John",
  "patronymic":  "Some",
  "surname":  "Doe",
  "phone":  "+37122145395",
  "email":  "bk@berweb.org",
  "email_verified":  1,
  "signup_complete":  1,
  "phone_verified":  1,
  "additional_phone":  null,
  "created_at":  "2020-05-16 18:11:08",
  "updated_at":  null
}
```
