# Chrome Unstable with Docker

Run chrome version Unstable through X11 socket.  
Highly inspired from https://github.com/jfrazelle/dockerfiles/blob/master/chromium/Dockerfile

Don't forget to allow docker instance to connect to your host. 

 * Quick solution (not secure-) `xhost +`
 * Advanced solution: See [here](http://olivier.barais.fr/blog/posts/2014.08.26/Eclipse_in_docker_container.html)

## Basic usage

```
docker run --rm -v /tmp/.X11-unix:/tmp/.X11-unix -e "DISPLAY=unix$DISPLAY" studiodev/chrome-unstable-x11  
```

## Advanced usage

Create image from Dockerfile

```
docker build -t chrome-unstable-x11 .
```

Create a new instance with one of these configurations  

*  Run with ephemeral storage  

```
docker run --rm -v /tmp/.X11-unix:/tmp/.X11-unix -e "DISPLAY=unix$DISPLAY" chrome-unstable-x11  
```

* Run stateful data-on-host  

```
docker run -d --name chrome-unstable -v /data/chrome:/data -v /tmp/.X11-unix:/tmp/.X11-unix -e "DISPLAY=unix$DISPLAY" chrome-unstable-x11  
docker start chrome-unstable-x11 # For next runs
```

*  Run with stateful dockerized container

```
docker run -d --volumes-from chrome-data -v /tmp/.X11-unix:/tmp/.X11-unix -e "DISPLAY=unix$DISPLAY" chrome-unstable-x11  
docker start chrome-unstable-x11 # For next runs  
```

Enjoy!
