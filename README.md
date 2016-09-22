# docker stats
## centreon
[![Docker Pulls](https://img.shields.io/docker/pulls/s4ntos/centreon.svg)](https://hub.docker.com/r/s4ntos/centreon/)
[![Docker Stars](https://img.shields.io/docker/stars/s4ntos/centreon.svg)](https://hub.docker.com/r/s4ntos/centreon/)

## centreon-poller 
[![Docker Pulls](https://img.shields.io/docker/pulls/s4ntos/centreon-poller.svg)](https://hub.docker.com/r/s4ntos/centreon-poller/)
[![Docker Stars](https://img.shields.io/docker/stars/s4ntos/centreon-poller.svg)](https://hub.docker.com/r/s4ntos/centreon-poller/)

# docker-centron

components for a docker instance does not include the mysql database 
the database needs to be instantiated separatly using the mariadb instance on docker registry

## usage steps

```
$ docker run --name centreon-mariadb -e MYSQL_ROOT_PASSWORD=pas5word -d mariadb 
$ docker run -d --name centreon-engine -p 80:80 centreon-engine
```
Access port 80 of the docker instance and configure the database and the centreon engine 

```
$ docker exec -ti centreon-engine bash
[image ] # mv /etc/supervisord_2.conf to /etc/supervisord.conf
```
And restart docker container

```
$ docker stop centreon-engine
$ docker start centreon-engine
```

## additional steps

requires the configuration of the connection to use the remote poller 

1. exchange keys between centron and the pooler 
2. create the poller
3. create the poller broker configuration
4. configure the poller engine > Data to use and additional broker module 
` /usr/lib64/nagios/cbmod.so /etc/centreon-broker/poller-module.xml `
5. apply all configuration to the poller
