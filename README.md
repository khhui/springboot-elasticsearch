# springboot-elasticsearch

### Pull elastic search image from Docker registry
Follow steps 1 to 7 (https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html)

### Create a network
```
docker network create elastic-net
```

### Run elasticsearch
```
docker run -p 127.0.0.1:9200:9200 -d --name elasticsearch --network elastic-net \
-e ELASTIC_PASSWORD=%ELASTIC_PASSWORD% \
-e "discovery.type=single-node" \
-e "xpack.security.http.ssl.enabled=false" \
-e "xpack.license.self_generated.type=trial" \
docker.elastic.co/elasticsearch/elasticsearch:8.14.1
```

### Run Spring application
```
mvn spring-boot:run
```