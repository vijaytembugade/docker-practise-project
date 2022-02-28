# commands for a docker

## To build docker image
docker build -t `name_for_docker_img` .


## Docker ignore
It is like ignoring node modules and *.md files
create file with dot. eg - .dockerignore* 

## List all images
docker image ls
docker images

## To run the image 
docker run `image_id` 
<we can use imge_name too>

docker run --name `container_name` `image_id`

## List of running containers
docker ps


## List of all containers
docker ps -a


## To start the docker container
docker start `container_id`

## To stop the docker container
docker stop `container_id`


### To map local port to the docker container port
docker run --name  `demo-docker_c2` -p 4000:4000 -d `image_id`

-d : ditached from the terminal 
-p : port local:docker

## re-start the container
docker start `container_id`


## Delete Images in docker
docker images rm `image_name` 

-f : force flag to forcefully stuff

## Delete the container
docker container rm `container_name`

## to delete all docker container and image
docker system prune -a

## docker build with version 
docker build -t `demo-docker:v1` .

## Volumes in docker
It is used to map the project folders and files directly with the docker container. It does not affect the on image.

volume flag `-v`

Note: In following example we used two volumes , one to map local to container all the files and another one is to do consisatncy in node_modules. 

Command :
docker run --name `contqainer_name` -p 4000:4000 --rm -v `path_to_local_folder`:`path_to_container_folder` -v `another_volume_to_ignore_node_modules` `image_name`

Example: 
docker run --name myapp_c_nodemon -p 4000:4000 --rm -v /home/vijay/Documents/docker/docker-crash-course-lesson-5/api:/app -v /app/node_modules myapp:nodemon



## docker --rm flag
Example 
`docker run --name myapp_c_nodemon -p 4000:4000 --rm myapp:nodemon`

This command create the container but when we stop it, it deletes the container. It is given before image name.


## Docker compose 
- It is a tool provided by docker
- we create `docker-compose.yaml` file in root directory and define the requirement 
- `docker-compose up` to run docker compose.
- `docker-compose down`  to make it down
- `docker-compose down -rmi all -v` to remove all the images created by docker-compose and volumns.
- 