# Frameworks para RESTAPI

- Django - Mais utilizado de longe (via pesquisa em vagas do StackOverflow/Glassdoor)
- Ideia é criar um container e colocar pra rodar na AWS ou GCP


## Setando container
- HOST SO - Debian
- Uname -a : `Linux krakken 4.9.0-8-amd64 #1 SMP Debian 4.9.144-3.1 (2019-02-19) x86_64 GNU/Linux`
- Step by Step:
    - sudo apt-get update
    - sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg2 \
        software-properties-common
    - curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
    - Check if you have the fingerprint `9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88`
        - sudo apt-key fingerprint 0EBFCD88
    - sudo add-apt-repository \
           "deb [arch=amd64] https://download.docker.com/linux/debian \
           $(lsb_release -cs) \
           stable"
    - sudo apt-get update
    - sudo apt-get install docker-ce docker-ce-cli containerd.io

### Cheat Sheet
#### List Docker CLI commands
docker
docker container --help

#### Display Docker version and info
docker --version
docker version
docker info

#### Execute Docker image
docker run hello-world

#### List Docker images
docker image ls

#### List Docker containers (running, all, all in quiet mode)
docker container ls
docker container ls --all
docker container ls -aq

docker build -t friendlyhello .  # Create image using this directory's Dockerfile  
docker run -p 4000:80 friendlyhello  # Run "friendlyhello" mapping port 4000 to 80  
docker run -d -p 4000:80 friendlyhello         # Same thing, but in detached mode  
docker container ls                                # List all running containers  
docker container ls -a             # List all containers, even those not running  
docker container stop <hash>           # Gracefully stop the specified container  
docker container kill <hash>         # Force shutdown of the specified container  
docker container rm <hash>        # Remove specified container from this machine  
docker container rm $(docker container ls -a -q)         # Remove all containers  
docker image ls -a                             # List all images on this machine  
docker image rm <image id>            # Remove specified image from this machine  
docker image rm $(docker image ls -a -q)   # Remove all images from this machine  
docker login             # Log in this CLI session using your Docker credentials  
docker tag <image> username/repository:tag  # Tag <image> for upload to registry  
docker push username/repository:tag            # Upload tagged image to registry  
docker run username/repository:tag                   # Run image from a registry  


docker stack ls                                            # List stacks or apps  
docker stack deploy -c <composefile> <appname>  # Run the specified Compose file  
docker service ls                 # List running services associated with an app  
docker service ps <service>                  # List tasks associated with an app  
docker inspect <task or container>                   # Inspect task or container  
docker container ls -q                                      # List container IDs  
docker stack rm <appname>                             # Tear down an application  
docker swarm leave --force      # Take down a single node swarm from the manager  


Fonte: https://docs.docker.com/get-started/part1/
