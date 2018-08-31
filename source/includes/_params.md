
# Instrument params

Запросить параметры инструментов.

> Пример:

```javascript
socket.send('[1104,[]]');
//Ответ
[1105,[
        [1,"BTCUSD",1,1,10000000,1,10000,1,0.075,-0.025,10,2,10,1,0,101,201,501,0,14400,28800,0],
        [5,"fBTCUSD_0618",1,1,10000000,1,10000,1,0.075,-0.025,10,2,10,2,1526781600,101,301,0,401,0,0,0.1],
        [101,"BTCUSDi",1,1,10000000,0,0,1,0,0,0,0,0,5,0,0,0,0,0,0,0,0],
        [201,"BTCUSDm",1,1,10000000,0,0,1,0,0,0,0,0,6,0,0,0,0,0,0,0,0],
        [301,"fBTCUSD_0618m",1,1,10000000,0,0,1,0,0,0,0,0,6,0,0,0,0,0,0,0,0],
        [501,"BTCUSDf_avg_8h",1,1,10000000,0,0,1,0,0,0,0,0,8,0,0,0,0,0,0,0,0]
      ]
]
```

### Request

<code>
[1104,[]]
</code>

### Response

<code>
[IsinId,Name,MinimumPriceIncrement,MinPrice,MaxPrice,MinOrderQuantity,MaxOrderQuantity,Precision,ComissTaker,ComissMaker,StepPrice,Maintenance,Leverage,Type,DataExp,IndexId,MarkPriceId,FundingIndexId,ExpirationIndexId,FundingBeginTime,FundingPeriodTime,ComissExpiration]
</code>

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
IsinId | true | uint16 | Код инструмента.
Name | true | string | Наименование инструмента.
MinimumPriceIncrement | true | int32 | Минимальный шаг цены.
MinPrice | true | int32 | Нижний лимит цены.
MaxPrice | true | int32 | Верхний лимит цены.
MinOrderQuantity | true | int32 | Минимальный размер заявки.
MaxOrderQuantity | true | int32 | Максимальный размер заявки.
Precision | true | int32 | Количество знаков после запятой.
ComissTaker | true | double | comiss_taker.
ComissMaker | true | double | comiss_maker.
StepPrice | true | int32 | step_price.
Maintenance | true | double | maintenance_k.
Leverage | true | int32 | Leverage.
Type | true | uint16 | Тип инструмента SWAP = 1, FUT = 2, OPT = 3, OPT_BIN = 4, INDEX = 5, MARK_PRICE = 6, AVG_INDEX = 7, AVG_INDEX2 = 8.
DateExp | true | uint64 | Дата экспирации.
IndexId | true | uint16 | IndexId.
MarkPriceId | true | uint16 | MarkPriceId.
FundingIndexId | true | uint16 | FundingIndexId.
ExpirationIndexId | true | uint16 | FundingIndexId.
FundingBeginTime | true | uint32 | FundingIndexId.
FundingPeriodTime | true | uint32 | FundingIndexId. 
ComissExpiration | true | double | ComissExpiration.

# Instrument statistics

Статистика инструментов.

> Пример:

```javascript
//Ответ
[1107,[
        [2,1651000,0,0,0,0],
        [1,112064,2,1814,1689611,0],
        [3,1651000,0,0,0,0],
        [4,1651000,0,0,0,0]
      ]
]
```

### Response

<code>
[IsinId,Price,Amount,Change24,Volume24,OpenInterest]
</code>

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
IsinId | true | uint16 | Код инструмента.
Price | true | int32 | Цена последней сделки.
Amount | true | int32 | Объем последней сделки.
Change24 | true | int32 | Изменение цены за 24 часа.
Volume24 | true | int64 | Объем торгов за 24 часа.
OpenInterest | true | int64 | Открытый интерес.














