 **RUN**: executes when BUILDING the image
 **CMD and ENTRYPOINT**: executes when the container starts

ENTRYPOINT determines  the main process we want to run, will be appended by command line when the docker contain is run
CMD: additional parameters we want to pass into entry point,  will overrided by command line when the docker contain is run

e.g. CMD
```
//container name=demo
FROM Ubuntu

CMD sleep 10
```
default command without specification (docker run demo): sleep 5
default command without specification (docker run demo sleep 10): sleep 10

e.g. ENTRYPOINT
```
//container name=demo
FROM Ubuntu

ENTRYPOINT ["sleep"]
```
default command without specification (docker run demo): error (no parameter)
default command without specification (docker run demo 10): sleep 10

e.g. CMD + ENTRYPOINT
```
//container name=demo
FROM Ubuntu
ENTRYPOINT ["sleep"]
CMD ["5"]
```
default command without specification (docker run demo): sleep 5
Command with specification (docker run demo 10): sleep 10