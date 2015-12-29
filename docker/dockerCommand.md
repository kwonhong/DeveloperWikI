##### 1. Creating Docker Machine Driver 
``` shell
# Setting CPU Count & Memory -- Virutal Driver name: kijiji-dev
docker-machine create --driver virtualbox --virtualbox-cpu-count "4" --virtualbox-disk-size "65536" --virtualbox-memory "4096" kijiji-dev
```
##### 2. Starting Docker Machine
``` shell
# Monitoring docker machins
docker-machine ls

# Starting the specific machine
docker-machine start <machine_name>

# Exporting all the required variable
docker-machine env  <machine_name>

# Evaluating
eval "$(docker-machine env <machine_name>)"

# If starting docker-machine for the first time, use this command
# docker-compose.yml file need to exists on the current directory
docker-compose up

# Monitoring Docker Machine
docker-compose ps
docker-compose start/stop

# Upgrading Docker Machine
docker-compose stop
docker-compose rm #Removing all docker running inside machine
docker-machine upgrade <machine_name>  #Upgrade
docker-machine compose up #Require docker-compose.yml & docker-machine env <machine_name>
```

##### 3. Trouble Shooting
###### 1. ~/.docker/machine/certs/ related problem
* Remove all the certs for docker
``` shell
rm -rf /Users/<user_name>/.docker/machine/certs
```
* Remove docker machine 
``` shell
docker-machine rm <machine_name>
```

* Create the machine again - You should see this kind of messages
  * Reference: https://docs.docker.com/machine/get-started/
``` 
Creating CA: /home/username/.docker/machine/certs/ca.pem
Creating client certificate: /home/username/.docker/machine/certs/cert.pem
```
