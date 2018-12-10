
# REST API for statistic data

Through the REST API, you can get statistical data on all stock instruments in the last 24 hours.

> Example:

```javascript
// Request  
https://api.bitex.one/v1/instruments

// Response
[{"btc_24h":109.38275895,"last_deal":26.031,"leverage":10,"maker_commission":-0.025,"name":"LTCUSDT","taker_commission":0.075,"type":"SWAP","usd_24h":391174.62},
{"btc_24h":99.1654167,"last_deal":107.45,"leverage":10,"maker_commission":-0.025,"name":"BCHABCUSDT-03.19","taker_commission":0.075,"type":"FUT","usd_24h":354635.36},
{"btc_24h":106.76572455,"last_deal":3561.8,"leverage":10,"maker_commission":-0.025,"name":"BTCUSDT-03.19","taker_commission":0.075,"type":"FUT","usd_24h":381815.58},
{"btc_24h":105.29687215,"last_deal":3573.2,"leverage":10,"maker_commission":-0.025,"name":"BTCUSDT","taker_commission":0.075,"type":"SWAP","usd_24h":376562.67},
{"btc_24h":91.2738902,"last_deal":95.58,"leverage":10,"maker_commission":-0.025,"name":"ETHUSDT","taker_commission":0.075,"type":"SWAP","usd_24h":326413.68},
{"btc_24h":99.0154287,"last_deal":108.66,"leverage":10,"maker_commission":-0.025,"name":"BCHABCUSDT","taker_commission":0.075,"type":"SWAP","usd_24h":354098.97},
{"btc_24h":109.22877655,"last_deal":2.021,"leverage":10,"maker_commission":-0.025,"name":"EOSUSDT","taker_commission":0.075,"type":"SWAP","usd_24h":390623.95},
{"btc_24h":91.5819756,"last_deal":96.64,"leverage":10,"maker_commission":-0.025,"name":"ETHUSDT-03.19","taker_commission":0.075,"type":"FUT","usd_24h":327515.46},
{"btc_24h":109.8624868,"last_deal":25.011,"leverage":10,"maker_commission":-0.025,"name":"LTCUSDT-03.19","taker_commission":0.075,"type":"FUT","usd_24h":392890.22},
{"btc_24h":109.2785538,"last_deal":2.0084,"leverage":10,"maker_commission":-0.025,"name":"EOSUSDT-03.19","taker_commission":0.075,"type":"FUT","usd_24h":390801.96}]
```

### Request

<code>
<a href='https://api.bitex.one/v1/instruments'>https://api.bitex.one/v1/instruments</a>
</code>

### Response

<code>
{"btc_24h":,"last_deal":,"leverage":,"maker_commission":,"name":,"taker_commission":,"type":,"usd_24h":}
</code>

Parameter | Required | Type | Description
--------- | ------- | ----- | -----------
btc_24h | true | uint32 | Last 24h turnover in BTC
last_deal | true | int32 | Last deal price of the instrument
leverage | true | uint16 | Leverage instrument
maker_commission | double | int32 | Comission of maker deal side in % (if negative then maker takes rebate)
name | true | string | Instrument name
taker_commission | double | int32 | Comission of taker deal side in %
type | true | uint8 | Type of instrument
usd_24h | true | uint32 | Last 24h turnover in USD



