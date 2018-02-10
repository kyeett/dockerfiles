


# Override curler_2 
CONSUL_SERVER_ADDR=192.168.0.11 docker-compose -f docker-compose.yaml -f docker-compose.override_curler_2.yaml up

# Override curler_2 and use external consul
CONSUL_SERVER_ADDR=192.168.0.11 docker-compose -f docker-compose.yaml -f docker-compose.overde_consul.yaml -f docker-compose.override_curler_2.yaml up


## Start server consul
docker run --rm  -p 8600:8600 -p 8301:8301 -p 8300:8300 --rm -p 8500:8500 --name deploy-consul consul agent -bootstrap -advertise=192.168.0.11 -client=0.0.0.0 -bind=0.0.0.0 -server -ui



https://www.consul.io/docs/guides/consul-containers.html