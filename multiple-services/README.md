
## Consul
#### Start local consul server
```
docker-compose -f consul/local_server.yaml up
```
#### Start consul client and join cluster
```
CONSUL_SERVER_ADDR=192.168.0.11 docker-compose -f consul/join_external.yaml up
```

## Overwriting
#### Things to try
1. What is the printout here?
```
docker-compose -f consul/local_server.yaml -f service_2/basic_printer.yaml up

service_2_1  | This should be overwritten
service_2_1  | This should be overwritten
service_2_1  | This should be overwritten

```
2. Add `-f service_2/overwriting_printer.yaml`. What is the printout here?
```
docker-compose -f consul/local_server.yaml -f service_2/basic_printer.yaml -f service_2/overwriting_printer.yaml up

service_2_1  | I have overwritten
service_2_1  | I have overwritten
service_2_1  | I have overwritten
```
3. Change the order, what is the printout here?
```
docker-compose -f consul/local_server.yaml -f service_2/overwriting_printer.yaml -f service_2/basic_printer.yaml up

service_2_1  | This should be overwritten
service_2_1  | This should be overwritten
service_2_1  | This should be overwritten
```

## Service depending on another service
#### Regular service that depends on consul
```

docker-compose -f consul/local_server.yaml -f service_1/waiting_for_consul.yaml up
```
