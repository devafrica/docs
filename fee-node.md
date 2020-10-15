# CryptoPayAfrica --Starting a Fee Node-- (CPA Coin)
##### Bringing Blockchain to Africa

[![Discord](https://img.shields.io/discord/471645937606066176?label=CryptoPayAfrica%20Discord)](https://discord.gg/HmTCVbS) [![GitHub contributors](https://img.shields.io/github/contributors-anon/devafrica/cpacoin?label=Contributors)](https://github.com/devafrica/cpacoin/graphs/contributors) [![GitHub issues](https://img.shields.io/github/issues/devafrica/cpacoin?label=Issues)](https://github.com/devafrica/cpacoin/issues) ![GitHub stars](https://img.shields.io/github/stars/devafrica/cpacoin?label=Github%20Stars)

### Join our many platforms and help us advance CPA 
![Twitter Follow](https://img.shields.io/twitter/follow/cpacoin1?style=social)
### CPA Coin Core Build Code and Fee node installation

**Cpa Coin Core**

![GitHub release (latest by date)](https://img.shields.io/github/v/release/devafrica/cpacoin)  
![GitHub All Releases](https://img.shields.io/github/downloads/devafrica/cpacoin/total)

  **Windows Gui Wallet Latest**
  ![GitHub release (latest by date)](https://img.shields.io/github/v/release/devafrica/cpa-wallet-proton)
 ![GitHub All Releases](https://img.shields.io/github/downloads/devafrica/cpa-wallet-proton/total)

Simplicity is one of our main goal and we will be adding some great features to our blockchain in the coming months and years ahead. We are 3 developers with a passion for blockchain. And yes… we do live in Africa!  
We would love for you to be part of our journey.
# What have we been up too!

  - We switched the origanal cryptonote core to fork TurtleCoin (Robust and Active core developement Community)
  - As you can see... some serious work to GitHub
  - Our Discordbot got a makeover go check out EmberBot
  - We are working on our explorers and gearing up for our exchange listing

### CPA Build Instructions

So you want to support the network and run a node?
You can run a fee node. This node will be picked up by our network as a supporting node for our wallets.
You can set your fee when you start your node and anyone using that node, the fee money will come to you.
So how do we get started?

1st things 1st. a Node can only be on a server that is available 24/7 and always online. Any nodes not deemed fit will be removed from the network.
You need to get a server 1st.
You can obtain one here.
https://m.do.co/c/2ce55fb45f2d

Once you registered your account go ahead and buy a droplet. They range from 5-50 USD a month. Please use a droplet with at least 2 gig ram and 40Gig drive space.
Your O.S should be Ubuntu 18 or 20.
There are a few things you should do before you follow the build instructions.
Make sure your droplet(server) is up-to-date.
run 
```sh
$ sudo apt-get update
$ sudo apt-get upgrade
```
Then proceed to build our coin from source see below and follow instructions.    https://github.com/devafrica/cpacoin
once the build is complete you can start the server for a test.
cd cpacoin/build/src
that should put you in the cpacoin directory.
we need to make a file to start our daemon 1st.
type nano daemon.sh
copy the following below into the file

#!/bin/sh
echo "running script"
./cpacoind --enable-cors "*" --rpc-bind-ip 0.0.0.0 --rpc-bind-port 13281 --enable-blockexplorer --enable-blockexplorer-detailed --fee-address cpZxRsnRTUe3riq6mW81RyRWx2BSNcU4Z51jnXUNivH27mRBCsP55vtcmfxpReLHtdF9FVBqvzQwAFgaWefKZWpa2ZqfoQMtu --fee-amount 550000

Of course replace your address with the one above.
hit Ctrl X and save the file.

now you can test and see if the file runs by typing.
./daemon.sh 
enter

This should start the daemon.
once its synced you can shut the daemon down for the following steps to complete.
we need to open your firewall.
We use ufw firewall program.

```sh
$ sudo apt-get install ufw
```
we need to add the following ports ....very important step.
```sh
$ ufw allow 22 (your ssh)
$ ufw allow 13281 (cpa com port)
$ enter
```

then type 

```sh
$ ufw enable
$ enter
```
it will come up with a warning about your current connection. if you did add port 22 you will be okay just say yes.

now we need to keep the daemon running even after restarting.
For this we are going to install a little program called pm2.

```sh
$ npm install -g pm2@latest
$ pm2 startup
$ pm2 start daemon.sh --name cpa-coin-daemon -i max (make sure you are in the cpacoin directory where the file is)
$ pm2 save
```
now you can start restart stop with the following commands.

```sh
$ pm2 start name cpa-coin-daemon
$ pm2 stop name cpa-coin-daemon
$ pm2 restart name cpa-coin-daemon
$ pm2 l (this will show what’s running and if its up or down).
```
That is it.... your node should be visible via the I.P.
http://your-ip:13281/info

You can create a domain name for it on the cpa network contact Siluro in discord for more info.
yourname.cryptopayafrica.org.za.

If we need to improve on this document please let us know on discord.
Goodluck and Welcome..



