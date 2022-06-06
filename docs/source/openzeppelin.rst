OpenZeppelin Cli
========

`Documentation`_ 

.. _Documentation: https://docs.openzeppelin.com/cli/2.8/


.. note::
    The development of this project has been discontinued. This short documentation therefore only exists for legacy reasons. 


Install 
------

``npm install @openzeppelin/contracts``

``npm install @openzeppelin/cli``

Create new project
----

``mkdir ProjctName && cd ProjectName``

``npm init -y``

``npx openzeppelin init``


OpenZeppelin Ethereum Packages
----


``npx oz link @openzeppelin/contracts-ethereum-package``

Deploy OpenZeppelin x Ganache 
-----


``npx ganache-cli --deterministic``

**Deploy**

``npx oz deploy``

**Interact**

``npx oz accounts``

``npx oz send-tx``

``npx oz balance --erc20 CONTRACTADDRESS```

**upgrade**

Change something. 

``px oz compile``

``npx oz upgrade``


