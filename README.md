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

```js
const {NodeClient, WalletClient} = require('bclient');
const {Network} = require('bcoin');
const network = Network.get('regtest');

const clientOptions = {
  network: network.type,
  port: network.rpcPort,
  apiKey: 'api-key'
}

const walletOptions = {
  network: network.type,
  port: network.walletPort,
  apiKey: 'api-key'
}

const client = new NodeClient(clientOptions);
const wallet = new WalletClient(walletOptions);

```


