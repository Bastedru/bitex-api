# Commands

Websocket API uses next commands

## Public request

Code | Name | Description
---------- | ------- | --------
1000 | AuthorizationRequest | Authorization request
1100 | SubscribeOrderBook | Subscribe to order book of a specific instrument
1101 | UnSubscribeOrderBook | Unsubscribe to order book of a specific instrument
1102 | SubscribeTrade | Subscribe to trades of a specific instrument
1103 | UnSubscribeTrade | Unsubscribe to trades of a specific instrument
1104 | InstrumentParamsRequest | Request all instrument parameters


## Public response

Code | Name | Description
---------- | ------- | --------
1 | OrderBookClearResponse | Clear order book of a specific instrument
2 | OrderBookSnapshotResponse | Snapshot of order book
3 | OrderBookIncrementalResponse | Incremental messages for order book
4 | TradeClearResponse | Clear trades of specific instrument
5 | TradeIncrementalResponse | Incremental messages for trades
1001 | AuthorizationResponse | Authorization response message
1105 | InstrumentParamsResponse | Request all instrument parameters
1107 | InstrumentStatisticResponse | Instrument statistic message

## Authorized request

Code | Name | Description
---------- | ------- | --------
100 | AddOrderRequest | Add order request
101 | MoveOrderNewVolumeRequest | Move order request
103 | CancelOrderRequest | Cancel order request

## Authorized response

Code | Name | Description
---------- | ------- | --------
110 | ClientOrderClearResponse | Clear client orders
111 | ClientOrderSnapshotResponse | Client orders snapshot
112 | PositionClearResponse | Clear client positions
113 | PositionSnapshotResponse | Client positions snapshot
114 | BalanceResponse | Client balance message
200 | AddOrderResponse | Add order error message
201 | MoveOrderNewVolumeResponse | Move order error message
203 | CancelOrderResponse | Cancel order error message