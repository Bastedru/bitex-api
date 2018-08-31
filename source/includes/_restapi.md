# REST API Reference

> Instruments params:

```javascript
curl "http://178.140.41.227:56914/api/public/params"
//Результат
[
        [3,"EURUSD",1,1,100000000,1,10000,5,0.075,-0.025,1,2,10],
        [4,"BCHBTC",1,1,100000000,1,10000,7,0.075,-0.025,1,2,10],
        [1,"BTCUSD",1,1,10000000,1,10000,1,0.075,-0.025,10,2,10],
        [2,"BCHUSD",1,1,100000000,1,10000,1,0.075,-0.025,10,2,10]
]
```

### Instruments params
<code>
GET /api/public/params
</code>

### Response instruments params

<code>
[IsinId,Name,MinStepPrice,MinPrice,MaxPrice,MinOrderQuantity,MaxOrderQuantity,Precision,comiss_taker,comiss_maker,step_price,maintenance_k,Leverage]
</code>

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
IsinId | true | int32 | Код инструмента.
Name | true | string | Наименование инструмента.
MinStepPrice | true | uint32 | Минимальный шаг цены.
MinPrice | true | int64 | Нижний лимит цены.
MaxPrice | true | int64 | Верхний лимит цены.
MinOrderQuantity | true | int64 | Минимальный размер заявки.
MaxOrderQuantity | true | int64 | Максимальный размер заявки.
Precision | true | int32 | Количество знаков после запятой.
comiss_taker | true | double | comiss_taker.
comiss_maker | true | double | comiss_maker.
step_price | true | uint64 | step_price.
maintenance_k | true | uint64 | maintenance_k.
Leverage | true | int32 | Leverage.