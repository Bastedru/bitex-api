
# Order

## Add Order

<aside class="warning">
Необходима авторизация!
</aside>

### Request

<code>
[100,[[ClientOrderId,IsinId,Price,Amount,Type]]]
</code>

> Add Order:

```javascript
//Поставить ордер на продажу
socket.send('[100,[[1,1,72051,-64,1]]]');
//Ответ фронт сервера
[200,[[1,300]]]
//Ответ матчинга, заявка выставлена
[100,[1,1,100000046,72051,-64,1,0,0,0,0,1526781600,0]]
```

```javascript
//Поставить ордер на продажу и покупку
socket.send('[100,[[1,1,72051,-64,1],[2,1,72050,64,1]]]');
//Ответ фронт сервера
[200,[[1,300],[2,300]]]
//Ответ матчинга
//Частичное исполнение заявки
[100,[1,1,100000047,72051,-64,2,230981,1649637,-50,-14,1526781600,2120]]
//Заявка полностью исполнена
[100,[1,1,100000047,72051,-14,2,230982,1649500,-14,0,1526781600,636]]
//Заявка выставлена
[100,[2,1,100000048,72050,64,1,0,0,0,0,1526781600,0]]
```

### Request parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ClientOrderId | true | uint32 | Внешний номер. Добавляется в заявку.
IsinId | true | int32 | Код инструмента.
Price | true | int64 | Цена заявки.
Amount | true | int64 | Количество единиц инструмента.
Type | true | uint8 | Вид заявки.

### Amount

<aside class="notice">
Amount < 0 order sell, Amount > 0 order buy
</aside>

### Type

Value | Description
--------- | ------- 
1 | Limit.
2 | Market.

<aside class="notice">
Если заявка типа Market то цена не учитывается.
</aside>

### Response validation

<code>
[200,[[ClientOrderId,Code]]]
</code>

### Response validation parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ClientOrderId | true | uint32 | Внешний номер. Добавляется в заявку.
Code | true | int32 | Код возврата.

### Response matching engine parameters

<code>
[100,[ClientOrderId,IsinId,OrderId,Price,Amount,Type,DealId,DealPrice,DealAmount,LeavesQty,Time,Fee]]
</code>

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ClientOrderId | true | uint32 | Внешний номер. Добавляется в заявку.
IsinId | true | uint16 | Код инструмента.
OrderId | true | uint64 | Код заявки в системе.
Price | true | int32 | Цена заявки.
Amount | true | int32 | Количество единиц инструмента.
Type | true | uint8 | Действие с заявкой.
DealId | true | uint64 | Идентификатор сделки.
DealPrice | true | int32 | Цена заключенной сделки.
DealAmount | true | int32 | Количество единиц инструмента в сделки.
LeavesQty | true | int32 | Оставшееся количество в заявке.
Time | true | uint64 | Время операции.
Fee | true | int32 | Комиссия.

### Type

Value | Description
--------- | ------- 
0 | Заявка удалена.
1 | Заявка добавлена.
2 | Заявка сведена в сделку.
3 | Заявка удалена, изменение заявки.
4 | Заявка удалена, экспирация.
5 | Заявка сведена в сделку, экспирация.
6 | Фондирование.
7 | DeleveregeDeal.
8 | LiquidationOrderAdd.
9 | LiquidationOrderDelete.
10 | LiquidationDeal.
11 | RiskOrderDelete.
12 | DeleverageOrderDelete.













## Move Order

<aside class="warning">
Необходима авторизация!
</aside>

### Request

<code>
[101,[[ClientOrderId,IsinId,OrderID,Price,Amount]]]
</code>

> Move Order:

```javascript
//Переместить ордер на покупку
socket.send('[101,[[2,1,100000048,72150,30]]]');
//Ответ фронт сервера
[201,[[2,300]]]
//Ответ матчинга, заявка удалена и выставлена
[100,[2,1,100000048,72050,64,3,0,0,0,0,1526781600,0]]
[100,[2,1,100000049,72150,30,1,0,0,0,0,1526781600,0]]
```

```javascript
//Переместить ордер на покупку и продажу
socket.send('[101,[[1,1,100000048,72051,-64,1],[2,1,100000047,72050,64,1]]]');
//Ответ фронт сервера
[201,[[2,300],[1,300]]]
//Ответ матчинга, заявки не найдены
[201,[[1,214],[2,214]]]
```

```javascript
//Переместить ордер на покупку и продажу
socket.send('[101,[[2,1,100000001,72150,30],[1,1,100000000,72051,-64]]]');
//Ответ фронт сервера
[201,[[2,300],[1,300]]]
//Ответ матчинга, заявки не найдены
[100,[2,1,100000001,72050,64,3,0,0,0,0,1526781600,0]]
[100,[2,1,100000002,72150,30,1,0,0,0,0,1526781600,0]]
//Ответ матчинга, заявки не найдены
[201,[[1,214]]]
```

### Request parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ClientOrderId | true | uint32 | Внешний номер. Добавляется в заявку.
IsinId | true | int32 | Код инструмента.
OrderID | true | uint64 | Код заявки в системе.
Price | true | int64 | Цена заявки.
Amount | true | int64 | Количество единиц инструмента.

### Response validation

<code>
[201,[[ClientOrderId,Code]]]
</code>

### Response validation parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ClientOrderId | true | uint32 | Внешний номер. Добавляется в заявку.
Code | true | uint8 | Код возврата.














## Cancel Order

<aside class="warning">
Необходима авторизация!
</aside>

### Request

<code>
[103,[[ClientOrderId,IsinId,OrderId]]]
</code>

> Cancel Order:

```javascript
//Снять ордер
socket.send('[103,[[1,1,100000002]]]');
//Ответ фронт сервера
[203,[[1,200]]]
//Ответ матчинга, заявка удалена
[100,[1,1,100000002,72150,30,0,0,0,0,0,1526781600,0]]
```

```javascript
//Снять ордера
socket.send('[103,[[1,1,100000003],[2,1,100000004]]]');
//Ответ фронт сервера
[203,[[1,200],[2,200]]]
//Ответ матчинга, заявки удалена
[100,[2,1,100000004,72050,64,0,0,0,0,0,1526781600,0]]
//Ответ матчинга, заявки не найдены
[203,[[1,214]]]
```

### Request parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ClientOrderId | true | uint32 | Внешний номер. Добавляется в заявку.
IsinId | true | int32 | Код инструмента.
OrderID | true | uint64 | Код заявки в системе.

### Response validation

<code>
[203,[[ClientOrderId,Code]]]
</code>

### Response validation parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ClientOrderId | true | uint32 | Внешний номер. Добавляется в заявку.
Code | true | uint8 | Код возврата.
