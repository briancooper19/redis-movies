# Spring Redis Movies 

This project contains multiple resources to explore and use SpringBoot + RediSearch + Redis JSON

High level arch: 
!["Redis Movies Overview"](./resources/images/architecture.png)

## Building and Running in Gitpod

Gitpod can spin up a fully featured developer friendly environment with both Visual Studio and Spring Redis Movies application running for you.

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/redis-projects/redis-movies)

1. Once the environment is available, the projects will compile, build containers and start with docker compose
2. You can use the Gitpod Visual Studio `TERMINAL` window to use docker compose as instructed below.
3. Wait a minute or so and Gitpod will detect the ports from the application (80, with an Nginx reverse proxy in front of the SpringBoot application on port 8080) and RedisInsight (8001) for you to access over the Gitpod web routing. You can check in the Gitpod Visual Studio `PORTS` window.
4. Make sure to select the `Open Browser` to open those.
5. Note: as we are loading ~10000 movies, the application may show empty while this loads. Make sure to refresh or check with RedisInsight.


## Working with Docker

There is a docker compose script which will bootstrap all the components required to make this demo work.

1. Run `docker compose up` from the root dir
2. The containers will start in the correct order
3. You can also selectively build with `docker compose build backend` for example
4. On startup:

- The Java Service will bootstrap `Redis-Stack` with 9876 movies
- - if needed, update the docker-compose env to disable: MOVIE_INSERT_ON_STARTUP=false
```bash
movie-service  | 2022-11-07 16:19:34.500  INFO 1 --- [main] io.redis.configuration.DataLoader        : Loading sample data movies file from dir : './' with the provided path : ./movies.json
movie-service  | 2022-11-07 16:19:35.445  INFO 1 --- [main] io.redis.configuration.DataLoader        : Loading 9897 movies into Redis
movie-service  | 2022-11-07 16:19:47.184  INFO 1 --- [main] io.redis.configuration.DataLoader        : Finished loading data into Redis
```

## Working with Projects locally

---
**NOTE**: Startup Procedure Required:
1. Start Redis-Stack `$ docker start redis-stack`
2. Start the Java Service `$ mvn spring-boot:run`
3. Start the frontend `$ yarn start`
4. ✨  Done
----

1. Redis Stack : https://redis.io/docs/stack/
2. Spring-Redis Java Movies Service ---> [Java Service](./spring-redis-search-om-api)
3. React Frontend Movies ---> [React Movies Site](./frontend)


### Software Reqs 

 - Docker 
 - Java 11+ 
 - NPM 8+
 - Node v18.7.0
 - Yarn 1.22.17+

### React Preview 

!["Redis Movies Overview"](./resources/images/redis-movies-overview.png)
