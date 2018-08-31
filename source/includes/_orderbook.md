# Order Book

> Order Book subscribe:

```javascript
//Подписаться на инструмент 1
socket.send('[1100, [1]]');

//Подписаться на инструмент 1 и 2
socket.send('[1100, [1, 2]]');
```

### Request Order Book subscribe
<code>
[1100,[IsinId]]
</code>

> Order Book unsubscribe:

```javascript
//Отменить подписку на инструмент 1
socket.send('[1101, [1]]');

//Отменить подписку на инструмент 1 и 2
socket.send('[1101, [1, 2]]');
```

### Request Order Book unsubscribe
<code>
[1101,[IsinId]]
</code>


### Response Order Book clear
<code>
[1,IsinId,[]]
</code>

> Order Book clear:

```javascript
[1,1,[]]
```

* Очистить все данные из книги заявок

### Response Order Book snapshot
<code>
[2,IsinId,[[Price,Amount]]]
</code>

> Order Book snapshot:

```javascript
[2,1,[
        [1622497,-21488],
        [1622498,-11753],
        [1622499,8598]
     ]
]
```

* Инициализировать книгу заявок

### Response Order Book incremental changes
<code>
[3,IsinId,[Price,Amount]]
</code>

> Order Book incremental changes:

```javascript
[3,1,[1622497,-2148]]
[3,1,[1622498,0]]
[3,1,[1622499,8248]]
```

* Обновить книгу заявок каджым изменением

### Order Book update logic 

* Если Amount = 0 означает, что уровень был **удален**.  
* Если Amount > 0 **обновить** объем по указанной цене **BID**.
* Если Amount < 0 **обновить** объем по указанной цене **ASK**.


