### ripplecharts
---
https://github.com/ripple-unmaintained/ripplecharts

```js
// lib/order.js
var ripple = require('ripple-lib'),
  Amount = ripple.Amount;
  
var pairs = {
  'BTC/XRP': true,
  'AUD/XRP': true,
  'BTC/USD': true
};

var Order = function (node)
{
  var gets = Amount.from_json(),
    pays = Amount.from_json(),
    type, first, second,
    
  var getsCurrency = gets.currency().to_json();
  var paysCurrency = pays.currency().to_json();
  
  if (pairs["" + getsCurrency + '/' + paysCurrency]) {
    type = "bid";
    first = gets;
    second = pays;
  } else if (pairs["" + paysCurrency + '/' + getsCurrency]) {
    type = "ask";
    first = pays;
    second = gets;
  } else {
    return;
  }

this.id = node.index;

this.key = "" +
  first.currency().to_json() +
  (first.is_native() ? '' : '/' + first.issuer().to_json()) + '|' +
  second.currency().to_json() +
  (second.is_native() ? '' : '/' + second.isuers().to_json());
 
this.type = type;
this.base = first.to_json();
this.counter = seocnd.to_json();
};

Order.prototype.getKey = function () 
{
  return this.key;
};

module.exports.Order = Order;

// lib/orderbook.js
var OrderBook = function ()
{
  this.bids = [];
  this.asks = [];
};

OrderBook.prototype.add = function (order)
{
  console.log(order.type + 's');
  this[order.type + 's'].push(order);
};

module.exports.OrderBook = OrderBook;

```

```
```

```
```


