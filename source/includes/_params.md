
# Instrument params

Request instrument parameters.

> Example:

```javascript
// Request
socket.send('[1104,[]]');
// Response
[1105,[
        [1,"BTCUSD",1,1,10000000,1,10000,1,0.075,-0.025,5,2,10,1,0,101,201,501,0,14400,28800,0],
        [13,"BCHUSD-12.18",1,1,10000000,1,10000,1,0.075,-0.025,10,2,10,2,1545998400000,102,313,0,402,0,0,0.1],
        [102,"BCHUSDi",1,1,10000000,0,0,1,0,0,0,0,0,5,0,0,0,0,0,0,0,0],
        [201,"BTCUSDm",1,1,10000000,0,0,1,0,0,0,0,0,6,0,0,0,0,0,0,0,0],
        [312,"BTCUSD-12.18m",1,1,10000000,0,0,1,0,0,0,0,0,6,0,0,0,0,0,0,0,0],
        [511,"EOSUSDf_avg_8h",1,1,10000000,0,0,3,0,0,0,0,0,8,0,0,0,0,0,0,0,0]
      ]
]
```

### Request

<code>
[1104,[]]
</code>

### Response

<code>
[ins_id,ins_name,tick_size,price_min,price_max,volume_min,volume_max,precision,comiss_taker,
comiss_maker,tick_value,maintenance,leverage,ins_type,expiration_time,index_id,mark_price_id,
funding_index_id,expiration_index_id,funding_begin_time,funding_period_time,expiration_comiss]
</code>

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ins_id | true | uint16 | Instrument identificator
ins_name | true | string | Instrument name
tick_size | true | int32 | Minimum price step
price_min | true | int32 | Minimum price limit
price_max | true | int32 | Maximum price limit
volume_min | true | int32 | Minimum order volume
volume_max | true | int32 | Maximum order volume
precision | true | int8 | Number of decimal places in the instrument price
comiss_taker | true | double | Deal commission for taker order, %
comiss_maker | true | double | Deal commission for maker order, %
tick_value | true | int32 | Cost of minimum price step
maintenance | true | double | Maintenance margin, %
leverage | true | uint8 | Leverage
ins_type | true | uint16 | Instrument type: <br>1 - Swap contract<br>2 - Futures contract<br>5 - Instrument price index<br>6 - Instrument mark price<br>7 - avg 30m price index (expiration price)<br>8 - avg 8h index (funding value index)
expiration_time | true | uint64 | Futures expiration time in ms, since Jan 01 1970. (UTC)
index_id | true | uint16 | Index price identificator
mark_price_id | true | uint16 | Mark price identificator
funding_index_id | true | uint16 | Funding index identificator
expiration_index_id | true | uint16 | Expiration index identificator
funding_begin_time | true | uint32 | Funding begin time in seconds since 12:00 AM (UTC)
funding_period_time | true | uint32 | Funding period time in seconds  
expiration_comiss | true | double | Expiration commission, %

# Instrument statistics

In first time after connect client receives statistics on all instruments. Then the data comes as it changes.

> Example:

```javascript
// Response
[1107,[
        [1,62735,33,-287,200203586,7638572],
        [16,4856,-15,-154,209799727,7873820],
        [102,4370,0,-332,0,0],
        [209,1829,0,-139,0,0],
        [301,62725,0,-464,0,0],
        [404,5114,0,-263,0,0],
        [509,1,0,1,0,0]
      ]
]
```

### Response

<code>
[ins_id,last_deal_price,last_deal_volume,change_24h,volume_24h,open_interest]
</code>

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
ins_id | true | uint16 | Instrument identificator
last_deal_price | true | int32 | Last deal price
last_deal_volume | true | int32 | Last deal volume
change_24h | true | int32 | Price change for the last 24 hours
volume_24h | true | int64 | Trade volume for the last 24 hours
open_interest | true | int64 | Open interest














