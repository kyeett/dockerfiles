# dockerfiles


# docker-compose files

| docker-compose        |            |
| ------------- |-------------|
| share-localhost | share localhost between dockerfiles, accessible at localhost:8500 |
| public-consul | Consul accessible from host or inside dockers at localhost:8500 |
| public-consul.overrider | Overrides curler_2. Usage:<br>`docker-compose -f docker-compose.yaml -f docker-compose.override_curler_2.yaml up`
 |
