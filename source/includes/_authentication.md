
# Authentication

Используйте ApiKey и приватный ключ для авторизации.

> Для авторизации используйте код:

```javascript
ApiKey = "ieW-nrNVN4qFJsMEiwtVqyjA";
Secret = "5fMhM8dqOzWs22heuSETNw_ED3BuXx_TBTboKJKlS8bFLIrm";

Nonce = "1510929522353"
Signature = HMAC_SHA256(Nonce, Secret)

socket.send('[1000,[ApiKey,Nonce,Signature]]');
//Ответ успешная авторизация
[1001,[200,"Welcome to bitex.one Realtime API."]]
//Ответ ошибка авторизации
[1001,[215]]
```

> Пример сообщения:

```javascript
socket.send('[1000,["ieW-nrNVN4qFJsMEiwtVqyjA","1510929522353","2e82ed97579f24976295cd895e071402c1776612015e15d1acff112885ae6c91"]]');
```

### Request

<code>
[1000,[ApiKey,Nonce,Signature]]
</code>

### Request parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ApiKey | true | string | API ключ авторизации.
Nonce | true | string | Nonce должно быть числом.
Signature | true | string | Подпись.

### Response

<code>
[1001,[Code,Message]]
</code>

### Request parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
Code | true | int32 | Код возврата.
Message | false | string | Nonce должно быть числом.








## Order Snapshot

После успешной авторизации клиент получает снепшот заявок

### Response clear

> Response Clear:

```javascript
//Очистка всех заявок
[110,[]]
```

<code>
[110,[]]
</code>

### Response snapshot

> Response Snapshot:

```javascript
//Снепшот всех заявок
[111,[[2,1,100000007,72050,64,1,1534029000],[1,1,100000005,720510000000,-64050000,1,1534029000]]]
```

<code>
[111,[[ClientOrderId,IsinId,OrderId,Price,Amount,Status,Time]]]
</code>

### Response parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ClientOrderId | true | uint32 | Внешний номер. Добавляется в заявку.
IsinId | true | int32 | Код инструмента.
OrderId | true | uint64 | Код заявки в системе.
Price | true | int64 | Цена заявки.
Amount | true | int64 | Количество единиц инструмента.
Status | true | uint8 | Действие с заявкой.
Time | true | uint64 | Время операции.

### Amount

<aside class="notice">
Amount < 0 order sell, Amount > 0 order buy
</aside>

### Status

Value | Description
--------- | ------- 
0 | Заявка удалена.
1 | Заявка добавлена.
2 | Заявка сведена в сделку.









## Position Snapshot

Снапшот позиций

### Response clear

> Response Clear:

```javascript
//Очистка всех позиций
[112,[]]
```

<code>
[112,[]]
</code>

### Response snapshot

> Response Snapshot:

```javascript
//Снепшот всех позиций
[113,[[1,1580441,-6297351]]]
```

<code>
[113,[[IsinId,PriceAvg,Amount]]]
</code>

### Response parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
IsinId | true | int32 | Код инструмента.
PriceAvg | true | int64 | Средняя цена входа.
Amount | true | int64 | Количество единиц инструмента.

### Amount

<aside class="notice">
Amount < 0 sell, Amount > 0 buy
</aside>





## Balance Snapshot

Снапшот баланса

### Response snapshot

> Response Snapshot:

```javascript
//Снепшот баланса
[114,[-18904990,99981095010,249210540,36157661133,49842108,-599400,99980495610,63590292585,0]]
```

<code>
[114,[RealisedPnL,WalletBalance,PositionMargin,OrderMargin,LiquidationPositionMargin,UnrealisedPnL,MarginBalance,AvailableBalance]]
</code>

### Response parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
RealisedPnL | true | int64 | профит по закрытым сделкам.
WalletBalance | true | int64 | Deposits - Withdrawals + RealisedPnL.
PositionMargin | true | int64 | маржа, зарезервированная под открытые позиции по всем инструментам.
OrderMargin | true | int64 | маржа, зарезервированная под все выставленные ордера по всем инструментам.
LiquidationPositionMargin | true | int64 | критический уровень маржи при достижении которого начинается ликвидация по всем позам.
UnrealisedPnL | true | int64 | суммарный профит профит по всем открытым позициям.
MarginBalance | true | int64 | WalletBalance + UnrealisedPnL.
AvailableBalance | true | int64 | WalletBalance - PositionMargin - OrderMargin + UnrealisedPnL.
ReferralProfit | true | int64 | Прибыль по реферальной программе.
