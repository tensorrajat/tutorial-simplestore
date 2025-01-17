Tutorial: Simple Store
======================

THIS IS MY FIRST CONTRIBUTION

*This file is very much a work in progress. This file is still under substantial
development. If you are new to Ethereum, this is likely not ready for you yet. It
is posted mostly to get some early feedback. Thanks!*

This is a simple tutorial to expose new blockchain developers to Ethereum
and ramp up existing blockchain developers with the [ethers.io](https://ethers.io)
ecosystem.

Simple Store is a simple on-chain contract which can store a single value. Anyone
may send a transaction to the Ethereum network to update this value.


Overview
--------

This tutorial provides a full, ready-to-use dApp, with deployment scripts, a test suite and
admin scripts. The initial contract we will be using has already been deployed to the
network.

We will then explore each component individually to update user interace, alter and deploy
a custom version of the Ethereum contract, and add test cases.


Before We Start
---------------

You must [install git](https://git-scm.com/downloads) and [install node.js](https://nodejs.org/en/download/) to follow this tutorial.

Once you have *node.js* installed, we can install the ethers toolchain. From your terminal, type:

```
/home/ricmoo> npm install -g ethers-cli
```

You may wish to [install Ganache](http://truffleframework.com/ganache/) for later steps, but that is not necessary for now.


Getting Started
---------------

In your terminal, from your home direcotry, we will download the tutorial
from GitHub and prepare our project.

```bash
# Download the Tutorial 
/home/ricmoo> git clone git@github.com:ethers-io/tutorial-simeplstore.git
Cloning into 'tutorial-simeplstore'...
remote: Counting objects: done
remote: Compressing objects: done.
Receiving objects: done.
Resolving deltas: done.

# Enter the Tutorial directory
/home/ricmoo> cd tutorial-simplestore

# Install the dependencies (ethers-cli, ethers)
/home/ricmoo/tutorial-simplestore> npm install
# ... This may be a few minutes, but you can ignore the output
```

Now that we have downloaded the tutorial and all of our dependencies, we
can start up our application.

```bash
# Start a local webserver to serve your dapp
/home/ricmoo/tutorial-simplestore> npm start
Serving content from file:///Users/ricmoo/Development/ethers/tutorials/simplestore
Listening on port: 8080
Local Application Test URL:
  mainnet: http://ethers.io/#!/app-link-insecure/localhost:8080/
  ropsten: http://ropsten.ethers.io/#!/app-link-insecure/localhost:8080/
  rinkeby: http://rinkeby.ethers.io/#!/app-link-insecure/localhost:8080/
  kovan:   http://kovan.ethers.io/#!/app-link-insecure/localhost:8080/        
```

The dapp is now running locally. Ethereum has multiple networks; a production network
(mainnet) and several test networks (ropsten, rinkeby, kovan). We will try out the dapp on
the Ropsten test network, so follow [this link](http://ropsten.ethers.io/#!/app-link-insecure/localhost:8080/) to load your dApp in ropsten.


Exploring Your Application
--------------------------

You may use any editor your are comfortable with. We are going to start
exploring the various files in the tutorial, before we start making changes.


## index.html

This is the front end to your application, made up of basic HTML, CSS and JavaScript.

The Application is currently very simple. We will get more into what each line
in the javascript does later, but basically we connect to an existing contract
on the blockchain using its **address** and its **Application Binary Interface** (ABI)
which is just a high-level description of what the functions and events the contract has.

## SimpleStore.sol

This is the Ethereum contract. We are currently using a version already deployed to the
Ethereum network, but will soon be making changes to it and deploying our own instances
to the blockchain.

## deploy-contract.js

This is a script we will use to help deploy our smart contract to the Ethereum network.
It is very simple for now, but will make it easier for us as our contract becomes more
complex.

## test-contract.js

This is our test suite. It is important to always test functionality of your contracts
since once they are deployed, they cannot be changed. Instead you have to re-deploy a
whole new instance and migrate your data and tools to use the new instance. It is better
to test thoroughly first.

The test cases are currently very basic, and we will be adding to them soon.

## simple-store.json

This file is automatically generated in the deploy-contract.js file. It contains
the address and the interface of the SimpleStore contract in a format that can
be eaily loaded by the ethers-app library.

## pacakge.json

This is a file used by *node.js* and *npm* to manage your applications dependencies and
handle some admin tasks.

-----

Exercises
=========

Now will will work through som simple exercises to familiarize ourselves with
how a dApp works.

Make the UI Prettier
--------------------

Add CSS transitions. Support pressing enter.

@TODO: Include code

Modify the Contract
-------------------

Make it charge ether to update the contract value.

@TODO: Include code

Add Test Cases
--------------

Add a test case for both sending sufficient ether to change the state and
insufficient ether which fails to update state.

@TODO: Include code and command lines to run tests

Debugging the Test Case
-----------------------

@TODO: Intentionally introduce a bug to demonstrate the real-time console.log

Deploy Updated Contract
-----------------------

@TODO: Include command lines to deploy the updated contract

-----

Sharing your Application
------------------------

Now that we are happy with our application on our local computer, we
can publish it to the internet for everyone to use.

Ethers.space is a free service provided by ethers to host small dApps
on  unique secure HTTPS URLs so that browser security content-policies
can keep you and your customers safe.

Ethers.space accounts are managed with standard Ethereum keys and do
not require a username or password.

Create a new private key to manage your ethers.space account.

```
/home/ricmoo/simplestore> ethers-deploy init
Do NOT lose or forget this password. It cannot be reset.
New Account Password: ******
Confirm Password: ******
Encrypting Account... (this may take a few seconds)
Account successfully created. Keep this file SAFE. Do NOT check it into source control
```

Make sure your latest changes are checked into the Git repo:

```
/home/ricmoo> git add index.html simple-store.json SimpleStore.sol
/home/ricmoo> git commit -m 'Updated my dApp.'
```

```
# Deploy your application to the internet
/home/ricmoo/simplestore> ethers-deploy publish
Sign Message:
    Message: ...
Sign Message? [y/n]: y

Successfully deployed!

Application URLs:
  Mainnet:  https://ethers.io/#!/app-link/0xf01ee6669078e5ec9a452fd60b7d18d41b53163e.ethers.space/
  Ropsten:  https://ropsten.ethers.io/#!/app-link/0xf01ee6669078e5ec9a452fd60b7d18d41b53163e.ethers.space/
  Rinkebey: https://rinkeby.ethers.io/#!/app-link/0xf01ee6669078e5ec9a452fd60b7d18d41b53163e.ethers.space/
  Kovan:    https://kovan.ethers.io/#!/app-link/0xf01ee6669078e5ec9a452fd60b7d18d41b53163e.ethers.space/
```

You may now share the Ropsten URL with your friends.

Advanced Exercises
==================

Working with Ganache (testrpc)
------------------------------

There may be times where you wish to test against a local node... Explain more here.

Run your Ganache development node on port 7545 (the default).

```
# Deploy the SimpleStore contract to your Ganache node
/home/ricmoo/simplestore> npm start -- --rpc http://localhost:7545 \
                          --local-accounts run deploy-contract.js 
```

Copy the `contract address` from the output of the above command and edit
`index.html`, placing your address in the `contractAddress` variable near the
top of the script tag.

```
# Run your local application against your Ganache node
/home/ricmoo/simplestore> npm start -- --rpc http://localhost:7545 serve
```

To import your first account from Ganache into ethers.io, copy your mnemonic
from the top of the Ganache UI. In the Ethers container, select add account,
then select import. Paste your mnemonic in the text field and follow the
instructions.

```
# Deploy your appliaction to the Ropsten testnet
/home/ricmoo/simplestore> ethers-deploy --network ropsten run deploy-contract
```

Update your `index.html` to point to the new contract on the ropsten network

```
# Run your local application against the Ropsten network (select the ropsten link below)
/home/ricmoo/simplestore> npm start
```

Once you are happy, you can publish to ethers.space.

```
# Run your local application against the Ropsten network (select the ropsten link below)
/home/ricmoo/simplestore> git init
/home/ricmoo/simplestore> git add index.html
/home/ricmoo/simplestore> git commit -m 'My first dapp.'
/home/ricmoo/simplestore> ethers-deploy publish
```


Deploying to Rinkeby and Kovan
------------------------------

@TODO

```
/home/ricmoo/simplestore> npm run deploy -- --network rinkeby
/home/ricmoo/simplestore> npm run deploy -- --network kovan
```
