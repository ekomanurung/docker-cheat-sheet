## Start Redis on Docker

### Redis single
- use `redis-single.yml` file to create container for redis single
- execute with command `docker-compose -f redis-single.yml up -d`, otherwise you can rename to `docker-compose.yml` and start without argument `-f filename.yml`

### Redis sentinel
- use `redis-sentinel.yml` file to create container for redis sentinel
- use command `docker-compose -f redis-sentinel.yml up --scale redis-sentinel=3 -d`
    - we will create redis-sentinel node = 3
- start to find which container is redis master
    - use `docker exec -it {redis_sentinel_container_name} /bin/sh`
        - if you didn't know which containers that running, run `docker ps`
    - use `redis-cli -p 26379`
    - type `info sentinel`
    - it will display the information regarding which ip that belongs to redis-master.
    - after that, run `redis-cli -h {host-from-info-sentinel} -p 6379`
    

### Version Downgrade and upgrade
- if you want to upgrade or downgrade your images version: 
    - `bitnami/redis:{your-version}` for redis single
    - `bitnami/redis-sentinel:{your-version}` for redis sentinel

- More information: https://hub.docker.com/r/bitnami/redis-sentinel/