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
[4,IsinId,[]]
</code>

> Trades clear:

```javascript
[4,1,[]]
```

* Clear all trades

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

* Initialize trades, avalable 100 last deals on instrument

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

* Update trades

### Trades update logic 

* If volume > 0 - **buy** deal (taker is buyer)
* If volume < 0 - **sell** dela (taker is seller)