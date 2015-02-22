# Chrome Unstable with Docker

Highly inspired from https://github.com/jfrazelle/dockerfiles/blob/master/chromium/Dockerfile

## Usage

```bash
# Create image
docker build -t chrome_unstable .

# Create a new instance with one of these configurations

# A. Run with ephemeral storage
docker run --rm -v /tmp/.X11-unix:/tmp/.X11-unix -e "DISPLAY=unix$DISPLAY" chrome_unstable

# B. Run stateful data-on-host
docker run -v /data/chromium:/data -v /tmp/.X11-unix:/tmp/.X11-unix -e "DISPLAY=unix$DISPLAY" chrome_unstable

# C. Run with stateful dockerized container
docker run --volumes-from chromium-data -v /tmp/.X11-unix:/tmp/.X11-unix -e "DISPLAY=unix$DISPLAY" chrome_unstable
```

Enjoy!