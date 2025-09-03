# install-geth-on-raspberry-pi-5-or-jetson-orin-nano
Steps to install geth on raspberry pi and jetson orin nano
## 
```bash
sudo apt update && sudo apt install -y build-essential git
```
## if "make all" = error than "do this"
```bash
---remove existing go
sudo apt remove golang-go
sudo apt remove --auto-remove golang-go
sudo rm -rf /usr/lib/go
sudo rm -rf /usr/local/go
```
## installing go version 1.21.6
```bash
wget https://go.dev/dl/go1.21.6.linux-arm64.tar.gz
sudo tar -C /usr/local -xzf go1.21.6.linux-arm64.tar.gz
export PATH=$PATH:/usr/local/go/bin
source ~/.bashrc
go version
---show: go version gol1.21.6 linux/arm64
```
## installing geth v1.13.12 stable
```bash
git clone https://github.com/ethereum/go-ethereum.git
cd go-ethereum
git checkout tags/v1.13.12 -b stable
-- installing go-ethereum
make all
-- check version
./build/bin/geth version

-- if fail do make than do "clean up"
cd go-ethereum
make clean
```
## config so that geth can be called from anywhere
```bash
nano ~/.bashrc
-- tambahkan di baris terakhir
export PATH=$PATH:/usr/local/go/bin
export PATH=$PATH:/home/iot-bc-jn-01/go-ethereum/build/bin
--
source ~/.bashrc

--- perintah untuk mencari geth dimana jika tidak yakin lokasinya dimana
find ~ -type f -name geth
```
