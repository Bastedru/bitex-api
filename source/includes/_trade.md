# Trades

> Trades subscribe:

```javascript
// Subscribe on trades for ins_id = 1
socket.send('[1102, [1]]');

// Subscribe on trades for ins_id = 1 and 2
socket.send('[1102, [1, 2]]');
```

### Request Trades subscribe
<code>
[1102,[ins_id]]
</code>

> Trades unsubscribe:

```javascript
// Unsubscribe on trades for ins_id = 1
socket.send('[1103, [1]]');

// Unsubscribe on trades for ins_id = 1 and 2
socket.send('[1103, [1, 2]]');
```

### Request Trades unsubscribe
<code>
[1103,[ins_id]]
</code>

### Response Trades clear
<code>
[4,ins_id,[]]
</code>

> Trades clear:

```javascript
[4,1,[]]
```

* Clear all trades

### Response trades snapshot
<aside class="notice">
Trades snapshot may be sended several separate messages
</aside>
<code>
[5,ins_id,[[price,volume,timestamp]]]
</code>

> Trades snapshot:

```javascript
[5,1,[
        [1620580,75,1513216484],
        [1620589,33,1513216784],
        [1620589,365,1513266784],
        [1620887,37,1513246631]
     ]
]
```

* Initialize trades, avalable 100 last deals of instrument

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ins_id | true | uint16 | Instrument ID
price | true | int32 | Deal price
volume | true | int32 | Deal volume
timestamp | true | uint64 | Deal time in sec, since Jan 01 1970. (UTC) 



### Response trades incremental changes
<code>
[5,ins_id,[[price,volume,timestamp]]]
</code>

> Trades incremental changes:

```javascript
[5,1,[
        [1619715,-4100,1513217115],
        [1619713,-876,1513217115],
        [1619713,5,1513217117]
     ]
]
```
* Update trades

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ins_id | true | uint16 | Instrument ID
price | true | int32 | Deal price
volume | true | int32 | Deal volume
timestamp | true | uint64 | Deal time in sec, since Jan 01 1970. (UTC)


### Trades update logic 

* If volume > 0 - **buy** deal (taker is buyer)
* If volume < 0 - **sell** dela (taker is seller)