# DCB-Credits API

### Шаги работы с API:
- Первым делом на странице со слайдером мы подтягиваем два API:
    - [`GET:/consumer-credit/calculator`](calculator?id=meta-data) - Подаём только валюту.
    - [`POST:/consumer-credit/calculator`](calculator?id=calculation) - Подаём данные в соответсвии с тем что пришло в первом запросе, а так-же данные по товару (цена итд..).
- Манипуляции подсчёта можем делать так-же запросом: `POST:/consumer-credit/calculator` с нужными данными.
- Если всё ок, то после уже оплаты первого взноса со стороны **buydo.com**, делаем запрос на создание заявки кредита. **Важно!! Только после успежной оплаты первого взноса!!**
- Если всё ок, то дозагружаем фото методом: `POST:/consumer-credit/verification-photos`.

### Дополнительно
Все цены подаются и возвращаются **не в копейках!**
- **Development API Url**: https://api.stage.yzcredits.com/
- **Production API Url**: https://api.yzcredits.com/
