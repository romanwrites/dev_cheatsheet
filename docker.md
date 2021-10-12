# Docker commands

delete container by port
```
docker rm -f $(docker ps | grep 5444)
```

run postgres in docker
```
docker run -e POSTGRES_DB=postgres -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres -p 5432:5432 -d postgres
```

delete container
```
docker rm -f CONTAINER
```
