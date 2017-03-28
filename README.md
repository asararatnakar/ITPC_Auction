clone the app in your fabric folder in Vagrant environment

cd /opt/gopath/src/github.com/hyperledger/fabric

```
git clone https://github.com/asararatnakar/ITPC_Auction
```

Vagrant Terminal 1:
--------------------
cd /opt/gopath/src/github.com/hyperledger/fabric

```
	orderer
```

Vagrant Terminal 2:
--------------------
cd /opt/gopath/src/github.com/hyperledger/fabric

```
	peer node start -o 127.0.0.1:7050
```

Vagrant Terminal 3:
--------------------

cd /opt/gopath/src/github.com/hyperledger/fabric

**Install**
```
	peer chaincode install -n mycc -p github.com/hyperledger/fabric/ITPC_Auction/art/artchaincode -c '{"Args":[""]}' -v 1
```

**Instantiate**
```
	peer chaincode instantiate -o 127.0.0.1:7050 -n mycc -c '{"Args":[""]}' -v 1
```

**Post User 100**
```
	peer chaincode invoke -o 127.0.0.1:7050 -n mycc -c  '{"Args":["iPostUser","100", "USER", "Ashley Hart", "TRD",  "Morrisville Parkway, #216, Morrisville, NC 27560", "9198063535", "ashley@itpeople.com", "SUNTRUST", "0001732345", "0234678", "2017-01-02 15:04:05"]}'
```

**Query User 100**
```
	peer chaincode query -o 127.0.0.1:7050 -n mycc -c '{"Args": ["qGetUser", "100"]}'
```

**Post Item 1000**
```
	peer chaincode invoke -o 127.0.0.1:7050 -n mycc -c '{"Args":["iPostItem", "1000", "ARTINV", "Shadows by Asppen", "Asppen Messer", "20140202", "Original", "landscape", "Canvas", "15 x 15 in", "art1.png","600", "100", "2017-01-23 14:04:05"]}'
```

**Query Item 1000**
```
	peer chaincode query -o 127.0.0.1:7050 -n mycc -c '{"Args": ["qGetItem", "1000"]}'
```

TODO: add other commands
