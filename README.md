# node-blockchain-js
Simple implementation of Crypto Blockchain using Node.js

## What is Blockchain?

A blockchain is an open, digital, and duplicated ledger of transactions. Each new transaction history is recorded and stored in an encrypted way that is very difficult to change or modify. A copy of this recorded information is sent a cross the blockchain network. Thus, making it highly secure.

It can be helpful to think of blockchains as augmented linked lists, or arrays in which each element points to the preceding array.
Within each block (equivalent to an element in an array) of the blockchain, there contains at least the following:

    1. A timestamp of when the block was added to the chain
    2. Some sort of relevant data. In the case of a cryptocurrency, this data would store transactions, but blockchains can be helpful in storing much more than just transactions for a cryptocurrency
    3. The encrypted hash of the block that precedes it
    4. An encrypted hash based on the data contained within the block(Including the hash of the previous block)

## Setup

```sh
npm i --save node-blockchain-js
```

## Usage

This module exposes 2 classes - 

    1. CryptoBlock
    2. CryptoBlockchain

```

const {CryptoBlockchain,CryptoBlock} = require("node-blockchain-js");

const myBlockchain = new CryptoBlockchain();

myBlockchain.addNewBlock(
  new CryptoBlock({
    sender: "Michael Scott",
    recipient: "Jim Halpert",
    quantity: 50
  })
);

myBlockchain.addNewBlock(
  new CryptoBlock({
    sender: "Dwight Schrute",
    recipient: "Andy Bernard",
    quantity: 100
  })
);

console.log(JSON.stringify(myBlockchain, null, 4));

//output 
{
    "blockchain": [
        {
            "index": 0,
            "timestamp": 1642749457405,
            "data": {
                "sender": "Michael Scott",
                "recipient": "Jim Halpert",
                "quantity": 50
            },
            "previousHash": " ",
            "hash": "e213edf7da7194c296231f1e0cfe9bc0b25ee4cf041832e2e3a7a8799a0e94dc"
        },
        {
            "index": 1,
            "timestamp": 1642749457427,
            "data": {
                "sender": "Dwight Schrute",
                "recipient": "Andy Bernard",
                "quantity": 100
            },
            "previousHash": "e213edf7da7194c296231f1e0cfe9bc0b25ee4cf041832e2e3a7a8799a0e94dc",
            "hash": "c8ffe31db108c2b9eb3bb05868f2b782fddf479bdd3e65aace12a36f39b1f5aa"
        }
    ]
}

```

