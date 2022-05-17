# create docker swarm service 
> sudo docker service create -p 80:80 --name php-webserver wahid74/phpcode

# list docker swarm service 
> sudo docker service ls

# list  container for service
> sudo docker ps -a