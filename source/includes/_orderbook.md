# Order Book
<aside class="notice">Order book available only on Swap contracts (ins_type=1) and Futures contracts (ins_type=2)</aside>
> Order Book subscribe:

```javascript
// Subscribe on order book for ins_id = 1
socket.send('[1100, [1]]');

// Subscribe on order book for ins_id = 1 and 2
socket.send('[1100, [1, 2]]');
```

### Request Order Book subscribe
<code>
[1100,[ins_id]]
</code>

> Order Book unsubscribe:

```javascript
// Unsubscribe on order book for ins_id = 1
socket.send('[1101, [1]]');

// Unsubscribe on order book for ins_id = 1 and 2
socket.send('[1101, [1, 2]]');
```

### Request Order Book unsubscribe
<code>
[1101,[ins_id]]
</code>


### Response Order Book clear
<code>
[1,ins_id,[]]
</code>

> Order Book clear:

```javascript
[1,1,[]]
```

* Clear all data on order book

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

* Initialize order book

### Response Order Book incremental changes
<code>
[3,IsinId,[price,volume]]
</code>

> Order Book incremental changes:

```javascript
[3,1,[1622497,-2148]]
[3,1,[1622498,0]]
[3,1,[1622499,8248]]
```

* Need update the volume in each price level of the order book

### Order Book update logic 

* If volume = 0 - **delete** price level on **ASK** and **BID** side
* If volume > 0 - **update** price level on **BID** side
* If volume < 0 - **update** price level on **ASK** side


