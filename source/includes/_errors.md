# Error codes

All API messages use the following error codes.

Code | Name | Description
---------- | ------- | --------
1 | Accept | Operation completed successfully
2 | WrongDataFormat | Wrong format of JSON
3 | InstrumentNotFound | Instrument not found in system
4 | LotLimitExceeds | Lot limit exceeds
5 | IncorrectLotStep | Lot must be integer type
6 | PriceLimitExceeds | Price value out of limit
7 | IncorrectPriceStep | Price is not a multiple of the minimum step
8 | IncorrectOrderType | Incorrect order type
9 | IncorrectClientOrderID | Incorrect value in client_order_id field
10 | IncorrectOrderID | Incorrect value in order_id field
11 | IncorrectFieldType | Incorrect field type
12 | TooMuchOrders | Too many orders in batch
13 | UnknownCommand | Uncnown command code
14 | AuthorizationRequired | Authorization required
15 | OrderNotFound | Order with order_id not found in system 
16 | AuthorizationError | Authorization error
17 | Liquidation | Liquidation process
18 | NoMoney | Not enoth money for operation
19 | OrderLessThanOne | Order volume less than one
20 | TradeDisabled | Trade disabled
21 | NotEnothLiquidity | Not enoth liquidity for operation
22 | MaxPosExceeds | Exceeds max position for current instrument
23 | FloodControl | Flood control points decreased to 0