
play-with-docker.com
Kernel Building Blocks
Docker Enginer
    Docker engine is modular

Docker controls control groups and namespaces

An image are a bunch of layers, losely connected with an image manifest. Manifest describes image and how to stack layers.
Laeyrs are independent and have no reference to each other. 
pulling an image is a two step process:
1. Get Manifest
2. Pull layers
Image Id is hash of the content of the image
There is a base layer

```dockerfile
docker image pull redis
docker history redit
docker image inspect redis
docker image remove redis

```
## Registry Explanation

Registry / Repo / Image(tag)
docker.io/redit
docker.io/`<repo>`latest
(default)          (default)
docker image pull docker.io/redis:4.0.1

docker image ls --digest

distribution hash is used to pull and push containers

docker image build -t psweb .
docker container run -d --name web1 -p 8080:8080 psweb

docker container should be located in the build context

### Building an image from a gir repo
docker image build -t psweb https://github.com/nigelpoulton/psweb.git
demon is pulling context from github repo

### Docker swirm
Swrm is a secure cluster of docker nodes
Every swirm has a leader manager
It can have a follower manager
When a manager is kiled, one of the leaders becomes a manager
Managers can be connected via a network

Manager Token and Worker Token 
You can your lock your swarm that prevents managers from re-joining
```dockerfile
docker swarm init
docker swarm join
docker swarm update --autolock=true
docker swarm unlock
docker swamr update --cert-expiry 48d
```





