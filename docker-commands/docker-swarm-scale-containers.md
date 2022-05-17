# create docker swarm service 
> sudo docker service create -p 80:80 --name php-webserver wahid74/phpcode

------------------------------------------------------
# scaling docker container on docker swarm
------------------------------------------------------

# scale up  service -> increase replica container
> sudo docker service scale php-webserver=4

# list docker swarm service 
> sudo docker service ls

# list  container for service
> sudo docker ps -a

# scale down service -> decrease replica container
> sudo docker service scale php-webserver=2

# list docker swarm service 
> sudo docker service ls

# list  container for service
> sudo docker ps -a