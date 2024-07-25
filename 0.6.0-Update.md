* Container ID öğrenelim

```console
docker ps -a
```

* Analog Conteiner'ı durdurup silelim

```console
docker stop (dockerID) && docker rm (dockerID)
```

* Güncelleme 😁

```console
docker pull analoglabs/timenode-test
```

```console
docker run -d -p 9944:9944 -p 30303:30303 -v $(pwd)/.analog:/.analog --name kaplangibi analoglabs/timenode-test --base-path /.analog --rpc-external --rpc-methods=Unsafe --unsafe-rpc-external --name (moniker)
```

* Ve sonuç 🐅

```console
docker restart (conteinerID)
```
