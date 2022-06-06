ETH Token with Truffle  
=======

1. Create Folder and initalize new project
-------

``truffle init`` 

2. add contracts in ``/contracts`` folder
----

For example: 

.. code-block :: python
    // SPDX-License-Identifier: MIT
    pragma solidity ^0.8.4;

    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

    contract MyToken is ERC20 {
        constructor() ERC20("MyToken", "MTK") {}
    }


3. Modify deployment files 

Note: they have to be named in a consecutive order. 

Your ``/migrations`` folder might look something like this: 

.. code-block :: python
    1_initial_migrations.js
    2_MyToken_migration.js
    ...


4. Create mnemonics
-------

``npx mnemonics``


5. Create secrets.json 
----

This file will store your newly created mnemonic

.. code-block :: js

    {
        "mnemonic": "repair derive axis lunch ********** shiver"
    }


5. Install `hdwallet-provider`_
-----
.. _hdwallet-provider: https://www.npmjs.com/package/@truffle/hdwallet-provider

You need this to sign the transaction. 

``npm install @truffle/hdwallet-provider``


6. Modify truffle-config.js
------

.. code-block :: js

    
    const HDWalletProvider = require('@truffle/hdwallet-provider');

    const mnemonic = require("./secrets.json").mnemonic;

    module.exports = {

    networks: {

        ropsten: {
        provider: () => new HDWalletProvider(mnemonic, `wss://speedy-nodes-nyc.moralis.io/30f9d049c*****941/eth/ropsten/ws`),
        network_id: 3,       // Ropsten's id
        gas: 5500000,        // Ropsten has a lower block limit than mainnet
        confirmations: 2,    // # of confs to wait between deployments. (default: 0)
        timeoutBlocks: 200,  // # of blocks before a deployment times out  (minimum/default: 50)
        skipDryRun: true     // Skip dry run before migrations? (default: false for public nets )
        },

    },

    // Set default mocha options here, use special reporters etc.
    mocha: {
    // timeout: 100000
    },

    // Configure your compilers
    compilers: {
        solc: {
        version: "0.8.13",      // Fetch exact version from solc-bin (default: truffle's version)
        // docker: true,        // Use "0.5.1" you've installed locally with docker (default: false)
        // settings: {          // See the solidity docs for advice about optimization and evmVersion
        //  optimizer: {
        //    enabled: false,
        //    runs: 200
        //  },
        //  evmVersion: "byzantium"
        // }
        }
    },

    };


7. Change default node provider
-------

Either use `Moralis`_ (Moralis Speedy Nodes) or `Infura`_ (New Project --> Settings)

``provider: () => new HDWalletProvider(mnemonic, `PASTE`)`` 

.. _Moralis: https://moralis.io/
.. _Infura: https://infura.io/


8. Enter Truffle Console 
-------

``truffle console --network ropsten``


9. Get accounts
-------

``await web3.eth.getAccounts()``


10. Fund account
------

**Get test ETH**

You'll need some `ETH`_ to deploy your contract later on. 

Transfer `ETH`_ to your first Truffle account vie `MetaMask`_. 

If you don't have a `MetaMask`_ account yet, create one now. 

.. _MetaMask: https://metamask.io/
.. _ETH: https://the-hitchhikers-guide-to-frequent-questions.readthedocs.io/en/latest/testnet.html 


11. Get balance of funded account
----

``await web3.eth.getBalance("ADDRESS")``


12. Migrate 
-----

This will deploy your contracts to your configured network. 

``migrate``

If you want to run all deployment files again ``migrate --reset``

13. Check Etherscan 
-----

**Get address**

To get the address of your smartcontract you must swap ``NAME`` for your contracts name. 

``NAME.address``

Now you can pad yourself on the back and lookup your contract on Etherscan. 


Truffle X OpenZeppelin 
------------

1. Import OZ contracts 

``import "@opzenzeppelin/..."``

2. Initalize project 

``npm init -y``

3. Install @openzeppelin/contracts 

``npm install @openzeppelin/contracts``

Note: this will create a nodes_modules folder in your repository. 

Errors
------

1. 

``Error: Could not find a compiler version matching 0.X.X. Please ensure you are specifying a valid version, constraint or build in the truffle config. Run `truffle compile --list` to see available versions.``

Note: this is for Mac

**Solution**

``sudo truffle compile``

Reason: truffle tries to compile into ``/usr/local/lib`` but has no permission 

2.

.. code:: yaml

    /usr/local/lib/node_modules/truffle/build/459.bundled.js:22386
        throw new Error(error);
    

    Uncaught Error: MyToken has no network configuration for its current network id (3).
        at Function.network (/usr/local/lib/node_modules/truffle/build/webpack:/packages/contract/lib/contract/properties.js:108:1)
        at Function.getter (/usr/local/lib/node_modules/truffle/build/webpack:/packages/contract/lib/contract/constructorMethods.js:285:1)
        at Function.get (/usr/local/lib/node_modules/truffle/build/webpack:/packages/contract/lib/contract/properties.js:129:1)
        ...

**Solution**

``sudo truffle console --network ropsten``

``migrate``
