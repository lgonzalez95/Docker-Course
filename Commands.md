## List Images
_docker images_

## Remove image
_docker rmi imageID_  
_docker rmi imageName:TAG_

## Build Image
_docker build -t ImageName:TAG -f DockerFileName ._

## List containers
_docker ps_

## Create container
_docker run -d --name containerName imageName:TAG_

## Create container with ports forwarding
_docker run -d -p localPort:servicePort --name containerName imageName:TAG_

docker run -d -p 9090:80 --name apache2 ubuntu_apache_from_image:v1

## Remove container
_docker rm name_

## COPY command
_COPY localFolder imageFolder_  
_Example: COPY html-template /var/www/html_

## ADD command
_ADD externalLink imageFolder_

## Create ENV variables: Use them to store repeted things
_ENV Key Value_

## WORKDIR 
_WORKDIR directory_

## Labels
Are used to store metadata  
_LABEL labelName_

## Open container using bash
_docker exec -ti containerName bash_
_docker exec -ti sample_container_with_template bash_

## Create user and add permissions
_RUN useradd userName_
_RUN chown userName:userName . -R_
_USER userName_

## Check container logs
_docker logs containerName_

## What is CMD?
_Allows a container to be alived, it identifies_
_which executable should be run when a container is started_

## Changing the context sample
_docker build -t sample_html:v5 -f Docker-Images/DockerFileWithWorkDirCommand --build-arg user=luis Docker-Images_

## Delete all dangling images
_docker rmi  $(docker images -f dangling=true -q)_

## Limit container memory
_docker run -d --name containerName --memory "200mb"_

## Limit container cpus
_docker run -d --name containerName --cpuset-cpus cpuRange_

## Copy files from docker host to the container and viceversa 
_docker cp pathToLocalFileInDockerHost containerName:pathToNewFileInTheContainer_
_docker cp containerName:pathToNewFileInTheContainer pathToLocalFileInDockerHost _

## Covert container to image
docker commit containerId imageBackUpName:TAG

## Destroy container automatically after we exit from the container
_docker run --rm -ti imageName bash_

## Create MySQL Bind volume
_docker run -d -v /tmp/mysql-volume:/var/lib/mysql --name mysql -e mysql:5.7_

## Create MySQL normal volume
_docker volume create volumeName_    
_docker run -d -v volumeName:/var/lib/mysql --name mysql -e mysql:5.7_

## Create anonymous volume
_docker run -d --name mysql -v /var/lib/mysql mysql:5.7_

## Delete all dangling volumes
docker volume rm $(docker volume ls -f=dangling=true -q)

## List docker networks
_docker network ls_

## Create network
_docker network create -d bridgeName --subnet IP/MASK  --gateway GATEWAY newNetworkName_
_docker network create -d bridge --subnet 172.18.0.0/16  --gateway 172.18.0.1 new_network_

## Remove network
_docker network remove networkName_

## Attach container to a network
_docker run -dti --network networkName --name containerName imageName_
_docker run -dti --network newNetwork --name container3 centos_

## Connect custom networks
_docker network connect NETWORKNAME CONTAINER_
_docker network connect newNetwork container5_

## Disconnect custom networks
_docker network disconnect NETWORKNAME CONTAINER_
_docker network disconnect newNetwork container5_

## Assign a static IP to a container
_docker run -dti --network NETWORK-NAME --ip IP-ADDRESS --name CONTAINER-NAME IMAGE-NAME_
_docker run -dti --network network-three --ip 172.20.0.100 --name container6 centos_

