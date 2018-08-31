# Trades

> Trades subscribe:

```javascript
//Подписаться на инструмент 1
socket.send('[1102, [1]]');

//Подписаться на инструмент 1 и 2
socket.send('[1102, [1, 2]]');
```

### Request Trades subscribe
<code>
[1102,[IsinId]]
</code>

> Trades unsubscribe:

```javascript
//Отменить подписку на инструмент 1
socket.send('[1103, [1]]');

//Отменить подписку на инструмент 1 и 2
socket.send('[1103, [1, 2]]');
```

### Request Trades unsubscribe
<code>
[1103,[IsinId]]
</code>

### Response Trades clear
<code>
[4,IsinId,[]]
</code>

> Trades clear:

```javascript
[4,1,[]]
```

* Очистить ленту сделок

### Response Trades snapshot
<code>
[5,IsinId,[Price,Amount,Timestamp]]
</code>

> Trades snapshot:

```javascript
[5,1,[1620580,75,1513216484]]
[5,1,[1619822,-1790,1513216586]]
[5,1,[1620887,37,1513216631]]
```

* Инициализировать ленту сделок, доступно 50 последних сделок по инструменту

### Response Trades incremental changes
<code>
[5,IsinId,[Price,Amount,Timestamp]]
</code>

> Trades incremental changes:

```javascript
[5,1,[1619715,-4100,1513217115]]
[5,1,[1619713,-876,1513217115]]
[5,1,[1619713,5,1513217117]]
```

* Обновить ленту сделок

### Trades update logic 

* Если Amount > 0 сделка на **покупку**.
* Если Amount < 0 сделка на **продажу**.