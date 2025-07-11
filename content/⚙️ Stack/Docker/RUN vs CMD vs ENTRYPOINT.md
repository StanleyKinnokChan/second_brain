 **RUN**: executes when BUILDING the image


 **CMD and ENTRYPOINT**: executes when the container starts

ENTRYPOINT determines  the main process we want to run, will be appended by command line when the docker contain is run
CMD: additional parameters we want to pass into entry point,  will overrided by command line when the docker contain is run


command line
```
# command can be run after the container started, here is sleep 5
docker run demo sleep 5

```

ENTRYPOINT (appending the command)
```
//container name=demo
FROM Ubuntu

ENTRYPOINT ["sleep"]
```
 docker run demos => error (because sleep command need a parameter!)
docker run demo 10  => sleep 10

if it is in docker compose, we should use:
docker-compose run --rm demo 10


CMD (default argument)
```
//container name=demo
FROM Ubuntu

CMD sleep 10
```
docker run demo => sleep 10
docker run demo sleep 5 => sleep 5 (overridden)
*To override, all the argument has to be used (aka sleep x)


CMD + ENTRYPOINT
```
//container name=demo
FROM Ubuntu
ENTRYPOINT ["sleep"]
CMD ["5"]
```
default command without specification (docker run demo): sleep 5
Command with specification (docker run demo 10): sleep 10

