## Instructions to build and run

```bash
docker build -t chrome .
```

```bash
# You will want the custom seccomp profile:

wget https://raw.githubusercontent.com/jfrazelle/dotfiles/master/etc/docker/seccomp/chrome.json -O ~/chrome.json
```

### macOS
```bash
open -a XQuartz

socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\"

docker run -it \
    --net host \
    --cpuset-cpus 0 \
    --memory 1024mb \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -e DISPLAY=<ip_address:0> \
    -v $HOME/Downloads:/home/chrome/Downloads \
    -v $HOME/.config/google-chrome/:/data \
    --security-opt seccomp=./chrome.json \
    --name chrome \
    chrome
```

### Linux
```bash
docker run -it \
    --net host \
    --cpuset-cpus 0 \
    --memory 512mb \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -e DISPLAY=unix$DISPLAY \
    -v $HOME/Downloads:/home/chrome/Downloads \
    -v $HOME/.config/google-chrome/:/data \
    --security-opt seccomp=./chrome.json \
    --device /dev/snd \
    --device /dev/dri \
    -v /dev/shm:/dev/shm \
    --name chrome \
    chrome
```
