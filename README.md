# 🧑‍🚀 Steps to Install geth on raspberry-pi-5 or jetson-orin-nano
Steps to install geth on raspberry pi and jetson orin nano
## 
```sh
sudo apt update && sudo apt install -y build-essential git
```
## if "make all" = error than "do this"
```sh
---remove existing go
sudo apt remove golang-go
sudo apt remove --auto-remove golang-go
sudo rm -rf /usr/lib/go
sudo rm -rf /usr/local/go
```
## 🧞 installing go version 1.21.6
```sh
wget https://go.dev/dl/go1.21.6.linux-arm64.tar.gz
sudo tar -C /usr/local -xzf go1.21.6.linux-arm64.tar.gz
export PATH=$PATH:/usr/local/go/bin
source ~/.bashrc
go version
---show: go version gol1.21.6 linux/arm64
```
## 🚀 installing geth v1.13.12 stable
```sh
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
## 👀 Config so that geth can be called from anywhere
```sh
nano ~/.bashrc
-- add these in the last lines
export PATH=$PATH:/usr/local/go/bin
export PATH=$PATH:/home/user-name/go-ethereum/build/bin
--
source ~/.bashrc

--- command to find geth location if not sure where it is
find ~ -type f -name geth
```
