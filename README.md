<p align="center">
</p>
<h1>
<p align="center"> Analog </p>
</h1>


* Minimum Sistem Gereksinimleri

```console
Hardware: 8 vCPUs, 16 GB Ram, 300 GB Disk
Network: Port 9944
Network: 500 MBps
Ubuntu version 20.04 ya da 22.04. Sorunsuz olsun diyorsan 22.04

"Benim Contabo Vps3'te çalışıyor. Yanında 5 tane daha node kurulu. Sync olduktan sonra sıkıntısız ilerliyor Analog."
```


*Güncellemeleri yapalım

```console
sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```

* Docker kuralım

```console
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```

* Docker bileşenlerini yükleyelim

```console
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

* Analog Timechain Docker görüntüsünü çekelim

```console
docker pull analoglabs/timechain
```

* Analog dizinini oluşturalım
```console
mkdir -p $(pwd)/.analog
```
### Analog docker container'ı çalıştıralım.
### Önemli: Moniker'i değiştirmeyi unutmayın. (Senin Telemetry üzerinde görünecek ismin. Daha sonra form doldururken bilgilere ekleyeceğiz bunu.) (Parantezleri uçur 😁)
```console
docker run -d -p 9944:9944 -p 30303:30303 -v $(pwd)/.analog:/.analog --name analog analoglabs/timechain --base-path /.analog --rpc-external --rpc-methods=Unsafe --unsafe-rpc-external --name (senin-moniker-ismin)
```
***Replace <your_moniker> with a unique name for your node. It must match the name you entered on your registration form***
### Install websocat
```
curl -LO https://github.com/vi/websocat/releases/download/v1.7.0/websocat_amd64-linux
chmod +x websocat_amd64-linux
sudo mv websocat_amd64-linux /usr/local/bin/websocat
```
### Verify websocat installation
```
websocat --version
```
***make sure version websocat 1.7.0***
### Test websocat with author_rotateKeys method
```
echo '{"id":1,"jsonrpc":"2.0","method":"author_rotateKeys","params":[]}' | websocat -n1 -B 99999999 ws://127.0.0.1:9944
```
### Check Telemetry
<a href="https://telemetry.analog.one/#/0x0614f7b74a2e47f7c8d8e2a5335be84bdde9402a43f5decdec03200a87c8b943">Telemetry</a>
***make sure your moniker***

### Provide link to Polkadot.js apps for further actions
<a href="https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc.testnet.analog.one###/accounts">Dashboard</a>
***input Rotating key in setup Node***

### Cheat sheet
```
docker logs -f analog
docker start analog
docker stop analog
docker rm analog
docker pull analoglabs/timechain
```


Hardware: 8 vCPUs (c6i.xlarge), 16 GB (c6i.xlarge), and at least 300 GB storage (NVMe SSD).
Network: Port 9944.
Network speed: At least 500 MBps.
OS: The Timechain Node has been developed and tested on x86_64 architecture. This guide will assume you’re using Ubuntu versions 18.04, 20.04, or 22.04.
