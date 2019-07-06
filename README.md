### bcoin
---
https://github.com/bcoin-org/bcoin

http://bcoin.io/api-docs/index.html

```js
'use strict';

var bcoin = require('bcoin');

var node = new bcoin.fullnode({
  network: 'testnet',
  db: 'memory'
});

(async function() {
  await node.open();
  await node.connect();
  
  node.on('connect', function(entry, block) {
    console.log('%s (%d) added to chain.', entry.rhash(), entry.height);
  });
  
  node.on('tx', function(tx) {
    console.log('%s added to mempool.', tx.txid());
  });
  
  node.startSync();
})();


```

```sh
git clone git://github.com/bcoin-org/bcoin.git
cd bcoin
npm install
./bin/bcoin
```

```
```


