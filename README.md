# Dockerfiles
a collection of useful dockerfiles


I am an idiot at times, and often never save or host my own docker images to dockerhub. 

Here are some tricks to restart and fix a number of issues with docker: 

To clear containers:

```
docker rm -f $(docker ps -a -q)
```

To clear images:

```
docker rmi -f $(docker images -a -q)
```
or
```
docker rm -v $(docker ps -a -q -f status=exited) 2>&1
docker rmi $(docker images -f "dangling=true" -q) 2>&1
```

To clear volumes:

```
docker volume rm $(docker volume ls -q)
```

To clear networks:

```
docker network rm $(docker network ls | tail -n+2 | awk '{if($2 !~ /bridge|none|host/){ print $1 }}')
```
