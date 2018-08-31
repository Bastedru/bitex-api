# Commands

API использует следующие коды команд:

## Public request

Code | Name | Description
---------- | ------- | --------
1000 | AuthorizationRequest | Запрос авторизации.
1100 | SubscribeOrderBook | Подписаться на книгу заявок.
1101 | UnSubscribeOrderBook | Отменить подписку на книгу заявок.
1102 | SubscribeTrade | Подписаться на ленту сделок.
1103 | UnSubscribeTrade | Отменить подписку на ленту сделок.
1104 | InstrumentParamsRequest | Параметры инструмента.


## Public response

Code | Name | Description
---------- | ------- | --------
1 | OrderBookClearResponse | Очистить книгу заявок.
2 | OrderBookSnapshotResponse | Снепшот книги заявок.
3 | OrderBookIncrementalResponse | Инкрементальное обновление книги заявок.
4 | TradeClearResponse | Очистить ленту сделок.
5 | TradeIncrementalResponse | Инкрементальное обновление ленты сделок.
1001 | AuthorizationResponse | Ответ авторизации.
1105 | InstrumentParamsResponse | Ответ параметры инструмента.
1107 | InstrumentChangeResponse | Ответ параметры торгов инструмента.

## Authenticated request

Code | Name | Description
---------- | ------- | --------
100 | AddOrderRequest | Добавление заявок.
101 | MoveOrderNewVolumeRequest | Перемещение заявок.
103 | CancelOrderRequest | Удаление заявок.

## Authenticated response

Code | Name | Description
---------- | ------- | --------
110 | ClientOrderClearResponse | Очистка всех заявок.
111 | ClientOrderSnapshotResponse | Снепшот всех заявок.
112 | PositionClearResponse | Очистка всех позиций.
113 | PositionSnapshotResponse | Снепшот всех позиций.
114 | BalanceResponse | Снапшот баланса.
200 | AddOrderResponse | Добавление заявок ответ.
201 | MoveOrderNewVolumeResponse | Перемещение заявок ответ.
203 | CancelOrderResponse | Удаление заявок ответ.