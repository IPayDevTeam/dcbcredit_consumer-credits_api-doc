# Verification Photos


<br>


## Photos existence

### GET `/consumer-credit/verification-photos/:clientId/existence`

Возвращает есть ли у пользователя загруженные фото или-же нет.

#### Query params:

| Param | Type | Description |
| --------- | ---- | ----------- |
| byExternalId `optional` | `0` или `1` | Выборка по ID из DCBanc или внутренней системы кредитов |

#### Route params:

| Param | Type | Description |
| --------- | ---- | ----------- |
| clientId | int | ID юзера из кредитов или из DCBanc |

#### Response:

```json
"data":  {
  "hasPhotos": false // boolean
}
```


<br>


## Photos uploading

### POST `/consumer-credit/verification-photos`

Загрузка и привязка фото к клиенту, позволяет загружать несколько картинок одним запросом. Имеет **2 варианта запроса** загружать фото.

Дополнение: привязывать картинки можно как к клиенту по его ID, так и к ID DCBanc.

1. Если привязывать к клиенту: то в запрос добавляем `clientId`.
2. Если привязывать к DCBanc: то в запрос добавляем `externalId`.

!>ВАЖНО! Не посылать два параметра одновременно.

#### Request:

**Способ 1:** Отправка обычной формы **multipart/form-data** в формате:

```json
files[] // Первый файл
files[] // Последующие файлы в таком-же формате
clientId // ID клиента к которому привязывать фото (после создания заявки ID клиента возвращается в ответе)
externalId // ID DCBanc (после подачи заявки к созданному клиенту подшиваются фото по ID из DCBanc)
```

<br>

**Способ 2:** Отправка стандартного **JSON** в котором картинки это массив из **base64** этих картинок:

```json
{
  "clientId": 12345, // ID клиента к которому привязывать фото (после создания заявки ID клиента возвращается в ответе)
  "externalId": 12412 // ID из DCBanc
  "files": [ // Массив base64 картинок
    "xxx",
    "xxx"
  ]
}
```

#### Response:

В случае успеха ответ пустой в **HTTP статусе 200**.
