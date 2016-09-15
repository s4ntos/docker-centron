# docker-centron

components for a docker instance does not include the mysql database 
the database needs to be instantiated separatly using the mariadb instance on docker registry

## additional steps

requires the configuration of the connection to use the remote poller 

1. exchange keys between centron and the pooler 
2. create the poller
3. create the poller broker configuration
4. configure the poller engine > Data to use and additional broker module 
` /usr/lib64/nagios/cbmod.so /etc/centreon-broker/poller-module.xml `
5. apply all configuration to the poller