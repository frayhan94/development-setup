
## Run containerized apps

* docker-machine create --driver virtualbox default
* If the machine is exist just run docker-machine start default
* docker-machine env default
* eval $(docker-machine env default)
* run docker-compose up
* If the image already build try to run this command
  docker-compose up --build


# Explanation of docker
* ADD . /code  
  Mount current directory to code directory on container folder
* volumes:
    - ./site.conf:/etc/nginx/conf.d/site.conf
   Mount site.conf file from local to /etc/nginx/conf.d/ in the container
   
       
## Open port 3000 for node

* Make sure before open the port the docker-machine is stopped
* VBoxManage modifyvm "default" --natpf1 "default,tcp,,3000,,3000"       

## Basic docker command 
* docker build -t my-node-app .
* If we already have the docker image we can kill it first to see the changes.
  docker kill my-node-app-container
* docker run -d -it --name=my-node-app-container -v $(pwd):/app -p 3000:3000 my-node-app

Examples:

  $ docker-machine-nfs test

    > Configure the /Users folder with NFS

  $ docker-machine-nfs test --shared-folder=/Users --shared-folder=/var/www

    > Configures the /Users and /var/www folder with NFS

  $ docker-machine-nfs test --shared-folder=/var/www --nfs-config="-alldirs -maproot=0"

    > Configure the /var/www folder with NFS and the options '-alldirs -maproot=0'

  $ docker-machine-nfs test --mount-opts="noacl,async,nolock,vers=3,udp,noatime,actimeo=1"

    > Configure the /User folder with NFS and specific mount options.

  $ docker-machine-nfs test --ip 192.168.1.12

    > docker-machine will connect to your host machine via this address
