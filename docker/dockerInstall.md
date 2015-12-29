#### Installation
##### 1. Docker Install
``` shell
# Downloading 0.4 version - Most recent version also works
curl -L https://github.com/docker/machine/releases/download/v0.4.0/docker-machine_darwin-amd64 > /usr/local/bin/docker-machine
```

##### 2. Docker-Compose Install
``` shell
# Downloading 1.4 version - Most recent version also works
curl -L https://github.com/docker/compose/releases/download/1.4.0/docker-compose-Darwin-x86_64 > /usr/local/bin/docker-compose
```

##### 3. Docker-Machine Install
``` shell
# Downloading 1.8 version - Most recent version also works
curl -L https://get.docker.com/builds/Darwin/x86_64/docker-1.8.0 > /usr/local/bin/docker
```

##### 4. Setting Proper Permission
* **User:** The user ("u"), the group ("g"), or other users ("o", also known as "world").
* **Operator:** Add ("+"), remove ("-") or explicitly set ("=").
* **State:** Readable ("r"), writable ("w"), or executable ("x")

``` shell
# Giving permission to everyone to execute
chmod ugo+x /usr/local/bin/docker
chmod ugo+x /usr/local/bin/docker-compose
chmod ugo+x /usr/local/bin/docker-machine
```

##### 5. Checking whether installation was successful
``` shell
docker -v
docker-compose -v
docker-machine -v
```

