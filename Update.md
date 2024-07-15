
* Analog kurulu olan docker yerini öğrenelim
```console
docker ps
```

* Analog fişini çekelim 🧨

* Analog DockerID kısımlarını kendinize göre değiştirin. (Parantezler uçuyor)

```console
docker stop (dockerID) && docker rm (dockerID)
```

* Full dosyasının fişini çekelim 🧨

```console
rm -rf /root/.analog/chains/anlogcc1/paritydb/full
```

* Snap çekelim

```console
curl -L https://analog-public.s3.amazonaws.com/backup/testnet-backup.tar.gz | tar -xz -C /root/.analog
```

* Docker'ı başlatalım. - Moniker isminiz aynı olmalı. (Parantezler 😁)

```console
docker run -d -p 9944:9944 -p 30303:30303 -v $(pwd)/.analog:/.analog --name analog analoglabs/timechain --base-path /.analog --rpc-external --rpc-methods=Unsafe --unsafe-rpc-external --name (senin-moniker-ismin)
```

* Logları kontrol edelim. Sync olmasını bekleyeceğiz. Tahmini olarak birkaç günümüzü alacaktır.
```console
docker logs -f analog
```

* Bugünlük bu kadardı. Keyifli günler 🐈
