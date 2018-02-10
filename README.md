# dockerfiles


## docker-compose files

| docker-compose        |            |
| ------------- |-------------|
| share-localhost | share localhost between dockerfiles, accessible at localhost:8500 |
| public-consul | Consul accessible from host or inside dockers at localhost:8500 |
| public-consul.overrider | Overrides curler_2. Usage:<br>`docker-compose -f docker-compose.yaml -f docker-compose.override_curler_2.yaml up`
 |


## Useful stuff

Start a public consul server 
```
docker run --rm  -p 8600:8600 -p 8301:8301 -p 8300:8300 --rm -p 8500:8500 --name deploy-consul consul agent -bootstrap -advertise=192.168.0.11 -client=0.0.0.0 -bind=0.0.0.0 -server -ui
```