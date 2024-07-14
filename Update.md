* Analog'da sorunlar yaşamıştık. Bugün bir güncelleme paylaştılar. Gelin beraber problemi çözelim.


* İlk olark bizi kurtaracak dosyayı indirelim

```console
curl -O https://analog-public.s3.amazonaws.com/backup/testnet-backup.tar.gz
```

* Analog kurulu olan docker yerini öğrenelim
```console
docker ps
```

* Analog fişini çekelim.
* Analog DockerID kısımlarını kendinize göre değiştirin. (Parantezler uçuyor)

```console
docker stop (dockerID) && docker rm (dockerID)
```

* Analog kurulu olan yere girelim
```console
cd .analog
```
* Chains klasörünün fişini çekiyoruz

```console
rm -rf ./chains/analogcc1/paritydb/full
```

* Tekrar root bölümüne dönelim

```console
cd
```

* İndirdiğimiz dosyayı fişini çektiğimiz dosyaya çıkartalım

```console
tar -xvzf testnet-backup.tar.gz -C .
chains/
chains/anlogcc1/
chains/anlogcc1/paritydb/
chains/anlogcc1/paritydb/full/
chains/anlogcc1/paritydb/full/table_01_b9
chains/anlogcc1/paritydb/full/table_01_39
```


* Docker'ı başlatalım. - Moniker isminiz aynı olmalı.

```console
docker run -d -p 9944:9944 -p 30303:30303 -v $(pwd)/.analog:/.analog --name analog analoglabs/timechain --base-path /.analog --rpc-external --rpc-methods=Unsafe --unsafe-rpc-external --name (senin-moniker-ismin)
```
