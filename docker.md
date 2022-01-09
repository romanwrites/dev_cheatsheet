# Docker commands

## Docker

### Delete container by port
```
docker rm -f $(docker ps | grep 5432 | cut -d " " -f 1)
```

### Run postgres in docker
```
docker run -e POSTGRES_DB=postgres -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres -p 5432:5432 -d postgres
```

## Delete container
```
docker rm -f CONTAINER
```

### Clear containers:
```
docker rm -f $(docker ps -a -q)
```
### Clear images:
```
docker rmi -f $(docker images -a -q)
```
### Clear volumes:
```
docker volume rm $(docker volume ls -q)
```
### Clear networks:
```
docker network rm $(docker network ls | tail -n+2 | awk '{if($2 !~ /bridge|none|host/){ print $1 }}')
```

### Clear all
```
docker system prune --all
```

### Get container id with name `postgres`
Stackoverflow [explanation](https://stackoverflow.com/a/34497614)  
```bash
docker ps -aqf "name=postgres"
```

### Remove container with name `postgres`
```bash
docker ps -aqf "name=postgres" | xargs -I{} docker rm -f {}
```

## Docker-compose
### Templates
[Templates](templates/docker/)
