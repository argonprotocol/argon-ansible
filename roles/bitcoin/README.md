Starts a bitcoin node with limited resources (no transaction relay, no wallet, no mining) and connects to the bitcoin network. This role will start with blockfilters enabled and an active rpc port so it can be used to monitor for spent utxos (and latest chain).

Creates a new signet with a private key. To create a new private key, run the following commands:
https://github.com/bitcoin/bitcoin/blob/master/contrib/signet/README.md

NOTE: if you are messing with this role, you will want to adjust the alias to use the conf and path (only when modifying signet:
```
alias bcli="sudo -u bitcoin ./bitcoin-cli -conf=/home/bitcoin/.bitcoin/bitcoin.conf"
```
