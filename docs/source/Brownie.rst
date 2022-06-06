ETH Token with Brownie 
=================

1. Create `venv`_
-------

.. _venv: https://the-hitchhikers-guide-to-frequent-questions.readthedocs.io/en/latest/Venv.html

2. Install 
------

**Solidity Compiler**

``npm install -g solc`` 

**Brownie**

``pip install eth-brownie``

or 

``pip3 install eth-brownie``

**Ganache**

``npm install -g ganache-cli`` 

**Web3.py**

``pip install web3``

4. Test
------

Check if brownie is properly set up: ``brownie``

You should see something like this: 

.. code-block:: python

    Brownie v1.18.1 - Python development framework for Ethereum

    Usage:  brownie <command> [<args>...] [options <args>]

    Commands:
    init               Initialize a new brownie project
    bake               Initialize from a brownie-mix template
    pm                 Install and manage external packages
    compile            Compile the contract source files
    console            Load the console
    test               Run test cases in the tests/ folder
    run                Run a script in the scripts/ folder
    accounts           Manage local accounts
    networks           Manage network settings
    gui                Load the GUI to view opcodes and test coverage
    analyze            Find security vulnerabilities using the MythX API

    Options:
    --help -h          Display this message
    --version          Show version and exit

    Type 'brownie <command> --help' for specific options and more information about
    each command.

5. Networks 
-------

List brownie networks: ``brownie networks list``

This will list all declared networks: 

.. code-block:: python

    Ethereum
    ├─Mainnet (Infura): mainnet
    ├─Ropsten (Infura): ropsten
    ├─Rinkeby (Infura): rinkeby
    ├─Goerli (Infura): goerli
    └─Kovan (Infura): kovan

    Ethereum Classic
    ├─Mainnet: etc
    └─Kotti: kotti

    Arbitrum
    └─Mainnet: arbitrum-main

    Avalanche
    ├─Mainnet: avax-main
    └─Testnet: avax-test

    Aurora
    ├─Mainnet: aurora-main
    └─Testnet: aurora-test

    Binance Smart Chain
    ├─Testnet: bsc-test
    └─Mainnet: bsc-main

    Fantom Opera
    ├─Testnet: ftm-test
    └─Mainnet: ftm-main

    Harmony
    └─Mainnet (Shard 0): harmony-main

    Moonbeam
    └─Mainnet: moonbeam-main

    Optimistic Ethereum
    ├─Mainnet: optimism-main
    └─Kovan: optimism-test

    Polygon
    ├─Mainnet (Infura): polygon-main
    └─Mumbai Testnet (Infura): polygon-test

    XDai
    ├─Mainnet: xdai-main
    └─Testnet: xdai-test

    Development
    ├─Ganache-CLI: development
    ├─Geth Dev: geth-dev
    ├─Hardhat: hardhat
    ├─Hardhat (Mainnet Fork): hardhat-fork
    ├─Ganache-CLI (Mainnet Fork): mainnet-fork
    ├─Ganache-CLI (BSC-Mainnet Fork): bsc-main-fork
    ├─Ganache-CLI (FTM-Mainnet Fork): ftm-main-fork
    ├─Ganache-CLI (Polygon-Mainnet Fork): polygon-main-fork
    ├─Ganache-CLI (XDai-Mainnet Fork): xdai-main-fork
    ├─Ganache-CLI (Avax-Mainnet Fork): avax-main-fork
    └─Ganache-CLI (Aurora-Mainnet Fork): aurora-main-fork


If you want more details, run: ``brownie networks list true``

If you want to add a new network to this list, run: ``brownie networks add [environment] [networkID] host=[host] chainid=[chainid]``

Rinkeby example: 

``brownie networks add Ethereum moralis-rinkeby host=https://speedy-nodes-nyc.moralis.io/70cbea161463fe***/eth/rinkeby chainid=4`` 

Don't know what to set ``host=`` to?

Either go to `Moralis`_ (Moralis Speedy Nodes) or `Infura`_ (New Project --> Settings) and get an endpoint.

.. _Moralis: https://moralis.io/
.. _Infura: https://infura.io/

This does not cover everything, so if you need more infos concering networks read this `article`_ or the offical `brownie documentation`_. 

.. _article: https://www.codeforests.com/2022/01/27/python-brownie-network-setup/
.. _brownie documentation: https://eth-brownie.readthedocs.io/en/stable/api-network.html

6. Create a token
---------

1. ``mkdir yourtoken``

2. ``cd yourtoken``

3. ``brownie bake token``

4. ``cd token`` 

Your file structure will now look something like this: 

.. code-block:: python

    /yourtoken 
        /token 
            /build
            /contracts 
            /interfaces 
            /reports
            /scripts
            /tests
            brownie-config.yaml
            requirements.txt


**Create Test Account**

``brownie accounts generate testaccount``

**Get test ETH**

You'll need some `ETH`_ to deploy your contract later on. 

If you don't have a `MetaMask`_ account yet, create one now. 

.. _MetaMask: https://metamask.io/
.. _ETH: https://the-hitchhikers-guide-to-frequent-questions.readthedocs.io/en/latest/testnet.html 

7. Deploy contract 
---------

``brownie compile``

**Modify scripts/token.py**

.. code-block:: python

    #!/usr/bin/python3

    from brownie import Token, accounts


    def main():
        acct = accounts.load('testaccount')
        return Token.deploy("Test Token", "TST", 18, 1e21, {'from': acct})

**Deploy contract**

``brownie run token.py --network NETWORKNAME``

Errors
-----

- FileNotFoundError: ``cd ./token``