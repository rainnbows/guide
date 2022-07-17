- docker --version => check version of docker
- docker search nginx   => search all nginx development
- docker pull nginx  => download nginx latest version
- docker pull nginx:1.20.2    => download with spacific version
- docker --version => check docker version
- docker --help    => show docker help using
- docker run --help => deep to command
- docker images     => check docker images in pc
- docker ps    => list container docker
- docker run nginx => (start docker nginx server)
- docker ps -a     => show container was runing
- docker restart container_name || id_container   => restart container by spacific name or id
- docker stop container_name || id_container => stop container by spacific name or id

- docker rm container_name || id   => want to remove container (example delete nginx)

- docker run --name myapp nginx   => run nginx as name myapp

- docker rm -f myapp   => remove container when it running (-f = force)

- docker run --name myapp -d nginx  => run nginx as name myapp with background process (-d = detach)

- docker run -p 80:80 --name myapp -d nginx   => run nginx as myapp with background process and map port local:80

- docker run -p 80:80 -v ~/myweb:/var/www/html --name myapp -d nginx   => run nginx as myapp with background process and map port local:80

- docker exec -it myapp bash     => interactive with nginx server
- cat /etc/nginx/conf.d/default.conf => check default location host

- ctrl + d    => exit container interactive

- docker start mynginx    => start nginx server
- docker stop mynginx     => stop nginx server

- docker create --name webserver nginx  => create and pull container
- docker start webserver   => start container
- docker rename webserver myserver  => rename container
- docker run -d -p 80:80 --name webserver nginx:1.20.2
- docker pause webserver
- docker unpause webserver


docker cp ./index.html webserver:/usr/share/nginx/html  copy file to container nginx

- docker run -p 80:80 -v ~/myweb1:/var/www/html --name myapp -d nginx   => run nginx as myapp with background process and map port local:8080  host to nginx server with port 80

- docker run -p 8080:80 -v ~/myweb2:/var/www/html --name myapp -d nginx   => run nginx as myapp with background process and map port local:8080  host server with other port 8080 

- docker ps -q  => show all id container running

- docker stop $(docker ps -q)   => stop all docker container running

- docker rm $(docker ps -aq)    => remove all docker container store or stop

- docker rmi nginx   => remove docker images nginx


- docker create --name web_service nginx  => create container
- docker start web_service
- docker rename web_service mywebservice  => rename container running without remove container
- docker pause web_service   => pause nginx server but still running
- docker unpause web_service  => unpause nginx
- docker port web_service   => check which port we config with service name

- docker cp ./index.html web_service:/usr/share/nginx/html   => copy file index to nginx server directory

- docker cp web_service:/etc/nginx/nginx.conf ./nginx.conf   => copy file from nginx service to local machine


-docker hostory images_name   => shown infomation of images hostory


============== docker bind Mount Volunm ===================

- docker run -it --name bind_mount type=bind,source="D:\docker",target=/app ubuntu   => we can asyn all document within folder local machine and docker marchine





============== create your own image and deploy to docker.hub ===================

- docker inspect nginx  => shown configuration in nginx




===============>   start docker with docker-compose file <=========================


=====> start <======

for wordpress

version: '3'

services:
  # Database
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
    networks:
      - tupleacademy
  # phpmyadmin
  phpmyadmin:
    depends_on:
      - db
    image: phpmyadmin/phpmyadmin
    restart: always
    ports:
      - '8080:80'
    environment:
      PMA_HOST: db
      MYSQL_ROOT_PASSWORD: password 
    networks:
      - tupleacademy
  # Wordpress
  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    ports:
      - '8000:80'
    restart: always
    volumes: ['./:/var/www/html']
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
    networks:
      - tupleacademy
networks:
  tupleacademy:
volumes:
  db_data:




  ======> end <=======

  using : docker-compose up
		: docker-compose up -d run background
		: docker-compose pause  pause container 
		: docker-compose unpause





============== docker file ===================

- create filename Dockerfile
	follow this text
	- FROM ubuntu
	- RUN apt-get update
	- RUN apt-install -y python3.7




========================================  project setup ==========================================

python -m venv env
pip freeze > requirement.tx


git .gitignore
	> env

remove __pycach__
export PYTHONDONTWRITEBYTECODE=1
