## Build and install Elicoin on Debian 8.x / Ubuntu 16.04.x

```sh
apt-get update && apt-get -y upgrade
apt-get -y install git build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils libboost-all-dev libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler libqrencode-dev
git clone https://github.com/elicoin/elicoin.git
cd elicoin
ELICOIN_ROOT=$(pwd)
BDB_PREFIX="${ELICOIN_ROOT}/db4"
mkdir -p $BDB_PREFIX
wget 'http://download.oracle.com/berkeley-db/db-4.8.30.NC.tar.gz'
echo '12edc0df75bf9abd7f82f821795bcee50f42cb2e5f76a6a281b85732798364ef  db-4.8.30.NC.tar.gz' | sha256sum -c
tar -xzvf db-4.8.30.NC.tar.gz
cd db-4.8.30.NC/build_unix/
../dist/configure --enable-cxx --disable-shared --with-pic --prefix=$BDB_PREFIX
make install
cd $ELICOIN_ROOT
./autogen.sh
./configure LDFLAGS="-L${BDB_PREFIX}/lib/" CPPFLAGS="-I${BDB_PREFIX}/include/"
make
make install
```
