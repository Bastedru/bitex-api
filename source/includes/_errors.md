# Errors

API использует следующие коды ошибок:

Code | Name | Description
---------- | ------- | --------
1 | Accept | Операция выполнена успешно.
2 | WrongDataFormat | Некорректный формат входных данных.
3 | InstrumentNotFound | Не найден соответствующий инструмент.
4 | LotLimitExceeds | Объем вне лимита.
5 | IncorrectLotStep | Объем не кратен минимальному шагу объема.
6 | PriceLimitExceeds | Цена вне лимита.
7 | IncorrectPriceStep | Цена не кратна минимальному шагу цены.
8 | IncorrectOrderType | Недопустимый тип заявки
9 | IncorrectClientOrderID | Некорректный тип данных.
10 | IncorrectOrderID | Некорректный тип данных.
11 | IncorrectFieldType | Некорректный тип данных.
12 | TooMuchOrders | Превышен лимит операций в пачке.
13 | UnknownCommand | Недопустимый тип сообщения.
14 | AuthorizationRequired | Нет прав для выполнения операции, необходимо авторизоваться.
15 | OrderNotFound | Не найдена заявка.
16 | AuthorizationError | Ошибка авторизации.
17 | Liquidation | Идет ликыидация позиции.
18 | NoMoney | Недостаточно средств.
19 | OrderLessThanOne | Ордер меньше или равен 0 после мува.
