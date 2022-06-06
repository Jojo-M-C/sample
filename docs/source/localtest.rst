Ganache 
========

Create new project
-------

see `ETH Token with Truffle`_ for futher instructions

.. _ETH Token with Truffle: https://the-hitchhikers-guide-to-frequent-questions.readthedocs.io/en/latest/Truffle.html

Install Ganache
-------

Terminal: 

``npm install --save-dev ganache-cli``

Software: 

`Download`_

.. _Download: https://trufflesuite.com/ganache/ 


Ganache determanistic
--------

``npx ganache-cli --deterministic`` 

Ganache will print out a list of available accounts and their private keys, along with some blockchain configuration values. Most importantly, it will display its address, which we’ll use to connect to it. By default, this will be  ``127.0.0.1:8545``
Keep in mind that every time you run Ganache, it will create a brand new local blockchain - the state of previous runs is not preserved. 

Deployment 
------

- Modify migration files. 

- Uncomment the following settings in **truffle-config.js**

.. code-block:: js

    module.exports = {
    ...
    networks: {
    ...
        development: {
        host: "127.0.0.1",     // Localhost (default: none)
        port: 8545,            // Standard Ethereum port (default: none)
        network_id: "*",       // Any network (default: none)
        },
        ...



Open new terminal and run ``truffle migrate``


Interacting with the local blockchain 
--------

``npx truffle console --network development``

Syntax 
------

See this `article`_ for ways to interact with your local blockchain. 

.. _article: https://docs.openzeppelin.com/learn/deploying-and-interacting 








