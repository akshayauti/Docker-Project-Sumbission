# IIEC RISE DOCKER PROJECT 2020
This Final Docker project submission Under **IIEC-RISE 1.0** Campaign. I learnt about Docker under the guidance of Vimal Daga Sir.

## I am explaining the set-up process in this documentation for my project.
## 1. My system setup:
* I am using **RedHat Enterprise Linux** on top of Windows using Oracle Virtual Box. also I have also installed Docker Software in it. .

## 1. Some basic commands use in docker are :
* Disabling firewall:
  * Firewall might block some networking stuffs that's why I at first stopped the firewall.
  * Use `systemctl stop firewalld`.
* Starting the docker:
  * Use `systemctl start docker` to start Docker Service.
* To stop Docker Service:
  * Use `exit` command if you are using container terminal.
* To see all the image running :
  * Use `docker ps` command.
* To see all the image running :
  * Use `docker ps` command.
* To see list of all the image :
  * Use `docker images` command
## 2. To Download the required images for Project(Optional Part if not download Then they automatically gets download when we run docker-compose file):
* Pulling MySQL Image:
  * Use `docker pull mysql:5.7` to download the mysql image to use as a database server.
  * explore more on https://hub.docker.com/_/mysql
* Pulling Joomla Image:
  * Use `docker pull joomla:3-php7.2-apache` we use this image because here we use apache server to deploy web pages also  this support php language.
  * explore more on https://hub.docker.com/_/joomla
  
## 3. Docker-Compose:
Here Docker-compose file is most important for the project in this file we store all the the project images setting also list of images used for the project. As to setup webapp we need both server and database so to connect server image to database image we use docker-compose.yml file
## Parameters use in docker-compose file:
### version:
   * This is version of Docker-Compose file. I used version 3.
### services:
   * In docker compose we use the term services to run the things iso which we mention inside services when we start the compose file.
### container name:
   * **dbos** and **joomladb** are the name of the containers which will be setup. Docker-compose automatically creates the name for the containers using our defined container name.
### image:
   * Here we specify the name of image to pull from hub.docker.com.
### restart:
   * this key is used if  any image we want to use fail to load due to any reason docker-compose will again restart it.
### volumes:
   * In docker as soon as we terminate an container our whole data inside that container destroyed. But if we want to make our data permanent then we have to use **docker volume**. Using the last volumes key we at first created two volumes. We know that MySQL and Joomla stores their data inside which folder. We simply make those folders permanent by mounting these volumes. That means due to any reason if our container terminated our data will not loose.Here I specify the location of the directories which is only used like `/var/lib/mysql` is location to save all files about database and `/var/www/html` here we store all php files.
   
### Port :
   * port is used to connect the container port to host port address if any request comes to external 8082 it will get transfered to port 80 of container in port: 8082:80  scenario
### environment:
   * There are many images in Docker which needs some pre-defined environment variables to run. That's why we need to pass these variables.

   
## 4. Docker-compose up:
  * Use `docker-compose up` to run the docker-compose file.


## 5. Docker-compose start/stop:
   * After using above command `docker-compose up` we can use  `docker-compose stop` to stop services. again to start the service use `docker compose start`. 

## 6. Docker-compose down:
  * Use `docker compose down` command to stop the Container.
