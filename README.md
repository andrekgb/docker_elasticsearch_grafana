# Reference
 - https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html
 - https://grafana.com/docs/grafana/latest/installation/configure-docker/

# Setting up local environment using Docker

1) Go to http://docker.com and install the software
2) Place the docker-compose.yaml file in a folder in your drive
3) Go to this folder in your terminal (mac) or cmd on windows
4) Create the folder `data/elastic` and `data/grafana` in the same folder where the `docker-compose.yml` is
5) Execute this command `docker-compose up -d`
6) wait for everything to download and then access : http://localhost:3000 . Grafana default credentials are admin/admin
7) Elastic Search will be available at http://localhost:9200

After you finish your days os work, or you just want to stop the running containers:
 - To Stop all containers: `docker stop $(docker ps -a -q)`

After you finish the project and you just want to delete the containers and its data:
 - To remove all containers and its data (be careful): `docker-compose down --volumes`
 
 ## Notes (docker)
 After you make the changes to the docker-compose file you'll have to 
 compile it again: `docker-compose up -d --build`
 
 ##Running commands inside the container
  - `docker exec -it <container_id_or_name> echo "I'm inside the container!"`
  - `docker exec -it grafana ls`
  
 ## How to find the internal network IP of the Elastic Search instance so you can connect with grafana
  - `docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' es01`
  You will need this when connecting Grafana to Elastic Search 
