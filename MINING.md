# Mining

## Pool mining
**Rtidcoin** can be mined only by CPU thanks to YescryptR16 hashing algorithm. GPU mining can be done too, but it is very slow and unefficient, that's why there is no GPU mining software available. This article is about how to mine Rtidcoin on CPU only.

### Mine Rtidcoin on Windows:

#### Mine with Rtidcoin GUI Miner:
- Download and install / unpack the latest version of [**Rtidcoin GUI Miner**](https://github.com/rtidcoin/rtidcoin-gui-miner/releases) for Windows from GitHub
- Run **Eliminer.exe**
- Set your wallet address and click on **Start mining** button

*Note that Rtidcoin GUI Miner is just a GUI for cpuminer-opt, it doesn't represent any additional advantage than user friendly interface.*

#### Mine with cpuminer-opt:
- Download the latest version of [**cpuminer-opt**](https://github.com/JayDDee/cpuminer-opt/releases) - Windows binary files (cpuminer-opt-x.x.x-windows.zip) and unzip the package.
- Run **cpuminer-opt** with following parameters:

```
cpuminer-sse2.exe -a yescryptr16 -o stratum+tcp://pool.rtidcoin.net:3333 -u [YOUR WALLET ADDRESS]
```

*These are the parameters for official Rtidcoin pool, you can use [**other Rtidcoin pool**](./POOLS.md) with different parameters as well.*  
*If Windows blocks your cpuminer-opt, please disable Microsoft Security Esentials or other antivirus / antispyware software.*

### Mine Rtidcoin on Linux:

#### Build cpuminer-opt on Linux (example for Debian 8.x):

```sh
apt-get update && apt-get upgrade
apt-get install build-essential libssl-dev libcurl4-openssl-dev libjansson-dev libgmp-dev automake screen ca-certificates wget tar
wget https://github.com/JayDDee/cpuminer-opt/archive/vx.x.x.tar.gz
tar xvzf vx.x.x.tar.gz
mv cpuminer-opt-x.x.x cpuminer
cd cpuminer
./build.sh
```
*x.x.x stands for actual version of cpuminer-opt.*  
*Version 3.8.x throws some error during compilation, please use 3.7.10 instead.*  
*This example doesn't work on Debian 9.x, other Linux distributions were not tested.*

#### Run cpuminer-opt on Linux:

```sh
./cpuminer -a yescryptr16 -o stratum+tcp://pool.rtidcoin.net:3333 -u [YOUR WALLET ADDRESS]
```
*These are the parameters for official Rtidcoin pool, you can use [**other Rtidcoin pool**](./POOLS.md) with different parameters as well.*

### Mine Rtidcoin on macOS:
- Download and install the latest version of [**XQuartz**](https://www.xquartz.org/)
- Download and install the latest stable version of [**Wine**](https://dl.winehq.org/wine-builds/macosx/download.html)
- Download and unpack the latest version of [**cpuminer-opt**](https://github.com/JayDDee/cpuminer-opt/releases) for Windows
- Run **cpuminer-sse2.exe** with parameters: **-a yescryptr16 -o stratum+tcp://pool.rtidcoin.net:3333 -u [YOUR WALLET ADDRESS]** under **Wine**

*These are the parameters for official Rtidcoin pool, you can use [**other Rtidcoin pool**](./POOLS.md) with different parameters as well.*  
***Rtidcoin GUI miner** for Windows might be working on macOS under Wine too (with **wine-mono** extension), but it was not tested yet.*

### Mine Rtidcoin on Android:

- Download and install [**AA Miner from Google Play**](https://play.google.com/store/apps/details?id=com.aaminer.miner)
- Run AA Miner
- Set algorithm to **yescryptr16**
- Pool address: **stratum+tcp://pool.rtidcoin.net:3333** (or any other pool address)
- User: [YOUR WALLET ADDRESS]
- Pass: nothing or "x"
- Tap on **Start mining**

## Solo mining
- Close your Rtidcoin Core wallet if still running
- Create **rtidcoin.conf** file in your Rtidcoin data directory if not exists

Default data location:

Operating system | Location
---------------- | --------
Windows | %APPDATA%\Rtidcoin
Linux: | ~/.rtidcoin/
macOS: | ~/Library/Application Support/Rtidcoin/

- Insert these lines to **rtidcoin.conf** file and then save it:

```
server=1
rpcuser=YOUR_USER_NAME
rpcpassword=YOUR_PASSWORD
rpcport=YOUR_PORT_NUMBER
```

- Run Rtidcoin Core wallet
- Download [**cpuminer-opt**](https://github.com/JayDDee/cpuminer-opt/releases) binaries or build it from sources.
- Run **cpuminer-opt** with following parameters:

On Windows:
```
cpuminer-sse2.exe -a yescryptr16 -o http://127.0.0.1:YOUR_PORT_NUMBER -u YOUR_USER_NAME -p YOUR_PASSWORD --coinbase-addr=YOUR_WALLET_ADDRESS
```

On Linux:
```
./cpuminer -a yescryptr16 -o http://127.0.0.1:YOUR_PORT_NUMBER -u YOUR_USER_NAME -p YOUR_PASSWORD --coinbase-addr=YOUR_WALLET_ADDRESS
```

## List of mining pools
Please see [**POOLS.md**](./POOLS.md) file.

## Hashrate benchmarks
Please see [**HASHRATE.md**](./HASHRATE.md) file.
