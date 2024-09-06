Starts a bitcoin node with limited resources (no transaction relay, no wallet, no mining) and connects to the bitcoin network. This role will start with blockfilters enabled and an active rpc port so it can be used to monitor for spent utxos (and latest chain).

Default is to connect to the testnet.

