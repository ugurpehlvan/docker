## node is initial layer of image, this will be downloaded from dockerhub (parent image)
## to add initial layer we must add FROM key word at the top if docker file
FROM node:17-alpine  

# will install nodemon globally
RUN npm install -g nodemon

# every command under this line will work on /app directory because we coppied all the source file inside app
WORKDIR /app

# this line will necassary for caching package.json file otherwise when we change our codebase 
COPY ./package.json .
# run this command on image to install dependencies (all dependecies will be loaded on image)
RUN npm install

# then we are creating the image of our source code
# The fist dot represent the copy from current directory, second dot is path inside the image, which we want to copy our soruce code. 
# COPY . /app => create app directory in the image and copy our source file inside it  (Example)
COPY . .

# The port that this container should listen on.
EXPOSE 4000

# all this command will prepare image for us to run it on container, image is just a blueprint for container it is not a running application
# for this reason we couldn't write RUN node app.js, because the code above are running in the built time and we are creating image for container to run it.
# container is a running application so we need to run node app.js file when container is running to do this we will add this command
# this means, run on container terminal=> node app.js 
# cmd will run code on runtime (when container is running)
CMD ["npm", "run", "dev"]


# to build image on docker desktop run =>  docker build -t myfirstimage . 
# docker images => lists all images
# to run container on terminal => docker run --name myapp_c1 myfirstimage (myfirstimage is image name, and myapp_c1 will be the container name for image)
# docker ps => will show running container
# docker ps -a => will show all contianer
# docker stop [containerName or ID]
# docker run --name mycontainer3 -p 4000:4000 -d myfirstimage => this will map container port to local computer port (-p means publish) (-d means don't block the terminal (detach mode))
# docker start [containerName or ID] will start the already build container
# docker image rm myimagename (myimagename is the image I want to delete or you can write image ID instead) docker image rm myimagename -f (force delete)
# docker container rm myapp_container (removes the container)
# docker system prune -a (this will remove all containers, all images and all volumes)
# docker build -t myapp:v1 . (will create and image with version)
# docker start myapp_c (docker run create brandly new container whereas docker start will start already existing)
# docker run --name myapp_c -p 4000:4000 --rm myimage (--rm removes the container when we stop it)
# docker run --name myapp_c -p 4000:4000 -v /Users/ugur/Desktop/projects/docker-course/api:/app myimage => # (-v means volume, which is used for mapping all the source folder (api) into the app folder (in image). Thus when anything changed in api file it is reflected to the app folder as well)
# to skip node_modules changes into container, we need to add anonoymous volumes.
# docker run --name myapp_c -p 4000:4000 -v /Users/ugur/Desktop/projects/docker-course/api:/app -v /app/node_modules myimage
# docker-compose up  // is combined command for docker
# docker-compose up --build  // build new image and run container
# docker-compose down (stops all the containers)
# docker-compose down --rmi all -v (--rmi-all removes all the image, -v remove volumes)
# docker login (to login docker hub)
# docker push ugurpehlivan/myapp_c (push images to the docker hub to share with other people)
# docker pull ugurpehlivan/myapp_c (download images from docker hub)
# docker logs [containerId] (logs the all running command when container launch)
# docker exec [containerId] -it redis-cli (this will help you to go in redis-cli server in docker)
# docker exec [containerId] -it sh (this will allow you to pass in any running container, open I shell in container) 
# if you are in a container you can exit from pressing "ctrl + d"
# docker run -it my_container sh (this will run my_container and then sh will allow you to open shell)

# docker compose ps (will show all the running containers)


# -------------- docker file schema
# 1 specify a base image
# 2 Install additional programs, dependencies etc.
# 3 specify command to run on container