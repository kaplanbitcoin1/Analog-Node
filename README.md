<p align="center">
</p>
<h1>
<p align="center"> Analog </p>
</h1>

<p align="center">
  <a href="https://www.analog.one/">Link</a> |
  <a href="https://discord.com/invite/analog">Discord</a> |
  <a href="https://x.com/OneAnalog">Twitter</a> |
  <a href="https://docs.analog.one/documentation/node-operators/introduction">Docs</a> 
</p>

> Hardware: 8 vCPUs, 16 GB, 300 GB Disk.
> Network: Port 9944.
> Network speed: 500 MBps.
> Ubuntu versions 20.04, ya da 22.04.

### - Complete the form  <a href="https://l5d87lam6fy.typeform.com/to/kwlADm6U">here</a>
### - Create a Polkadot wallet for stash account using the Subwallet extension
### - Request Faucet in Discord

### Update and install necessary packages
```
sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```
### Add Docker GPG key and repository
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```
### Install Docker and related components
```
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
### Pull the Analog Timechain Docker image
```
docker pull analoglabs/timechain
```
### Create directory for Analog
```
mkdir -p $(pwd)/.analog
```
### Run the Analog Timechain Docker container
```
docker run -d -p 9944:9944 -p 30303:30303 -v $(pwd)/.analog:/.analog --name analog analoglabs/timechain --base-path /.analog --rpc-external --rpc-methods=Unsafe --unsafe-rpc-external --name <youe_moniker>
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

