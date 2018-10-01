
# Authentication

Use ApiKey and private key for authorization.

> For authorization use this code:

```javascript
ApiKey = "ieW-nrNVN4qFJsMEiwtVqyjA";
Secret = "5fMhM8dqOzWs22heuSETNw_ED3BuXx_TBTboKJKlS8bFLIrm";

Nonce = "1510929522353"
Signature = HMAC_SHA256(Nonce, Secret)

socket.send('[1000,[ApiKey,Nonce,Signature]]');
// Authorization success response
[1001,[1,"Welcome to bitex.one Realtime API."]]
// Authorization error response
[1001,[16]]
```

> Example message:

```javascript
socket.send('[1000,["ieW-nrNVN4qFJsMEiwtVqyjA","1510929522353","2e82ed97579f24976295cd895e071402c1776612015e15d1acff112885ae6c91"]]');
```

### Request

<code>
[1000,[api_key,nonce,signature]]
</code>

### Request parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
api_key | true | string | API key
nonce | true | string | Nonce must be a number
signature | true | string | Signature

### Response

<code>
[1001,[code,message]]
</code>

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
code | true | uint8 | Result code
message | false | string | Message string




## Order Snapshot

If authorization succeed client gets orders snapshot

### Response clear

> Response Clear:

```javascript
// Clear all client orders
[110,[]]
```

<code>
[110,[]]
</code>

### Response snapshot

> Response Snapshot:

```javascript
// All orders snapshot
[111,[
        [2,1,100000007,72050,64,1,1534029000],
        [1,1,100000005,720510000000,-64050000,1,1534029000]
     ]
]
```

<code>
[111,[[client_order_id,ins_id,order_id,price,volume,status,time]]]
</code>

### Response parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
client_order_id | true | uint32 | Client defined order id
ins_id | true | uint16 | Instrument ID
order_id | true | uint64 | System order ID
price | true | int32 | Order price
volume | true | int32 | Order volume in contracts
status | true | uint8 | Order status
time | true | uint64 | Time of last order change in sec, since Jan 01 1970. (UTC) 

### Volume

<aside class="notice">
If volume < 0 - sell order. If volume > 0 - buy order
</aside>

### Status

Value | Description
--------- | ------- 
0 | Order canceled
1 | Order added
2 | Order executed









## Position Snapshot

If authorization succeed client gets positions snapshot

### Response clear

> Response Clear:

```javascript
// Clear all client positions
[112,[]]
```

<code>
[112,[]]
</code>

### Response snapshot

> Response Snapshot:

```javascript
// Snapshot all client positions
[113,[
        [9,18462520000001,-2000],
        [1,630330330000000,1000]
     ]
]
```

<code>
[113,[[ins_id,price_avg,volume]]]
</code>

### Response parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ins_id | true | uint16 | Instrument identificator
price_avg | true | int64 | Average price multiplied by 10^10
volume | true | int32 | Position volume

### volume

<aside class="notice">
volume < 0 - short position, volume > 0 - long position
</aside>





## Balance Snapshot

All balance values in satoshi (1 satoshi = 0.00000001 BTC).

### Response snapshot

> Response Snapshot:

```javascript
// Balance snapshot
[114,[2480662205,5754608835,35127000,0,7025400,-810125,5753798710,5718671710,2963326]]
```

<code>
[114,[realized_pnl,wallet_balance,position_margin,order_margin,maintenance_margin,<br>
unrealized_pnl,margin_balance,available_balance,referral_profit]]
</code>

### Response parameters

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
realized_pnl | true | int64 | Realized profit and loss
wallet_balance | true | int64 | Funds on account exclude unrealized_pnl
position_margin | true | int64 | Margin, reserved by all open positions
order_margin | true | int64 | Margin, reserved by all active orders
maintenance_margin | true | int64 | Critical level of margin. When wallet_balance < maintenance_margin liquidation begins
unrealized_pnl | true | int64 | Sum profit by all open positions
margin_balance | true | int64 | wallet_balance + unrealized_pnl
available_balance | true | int64 | wallet_balance - position_margin - order_margin + unrealized_pnl
referral_profit | true | int64 | Refferal program profit
