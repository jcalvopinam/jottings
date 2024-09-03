# Docker useful commands

## General considerations
- If you don't specify the port, it's not going to open up any ports at all in your local machine

---
## Instances
### List Instances
```sh title:command
docker ps -a
```

### Start instance
- To start some instances is required named with spaces
```sh title:command
docker start <name|container-id> <name|container-id>

# sample
docker start my-instance-name1 my-instance-name2
# or
docker start aae2f44c8c19 af8c0ab27b5b
```

### Stop instance
- To stop some instances is required named with spaces
```sh title:command
ddocker stop <name|container-id> <name|container-id>

# sample
docker stop my-instance-name1 my-instance-name2
# or
docker stop aae2f44c8c19 af8c0ab27b5b
```

### Run instance
```sh title:command
docker run -p <external-port:internal-port> <image-name|image-id>:<version>

# sample
docker run -p 3306:3306 mysql:8
```

#### Run instance detach 
```sh title:command
docker run -d -p <external-port:internal-port> <image-name|image-id>:<version>

# sample
docker run -d -p 3306:3306 mysql:8
```

#### Run named instance detach 
```sh title:command
docker run --name <instance-name> -d -p <external-port:internal-port> <image-name|image-id>:<version>

# sample
docker run --name my-instance-name -d -p 3306:3306 mysql:8
```

#### Run instance with environment variables
- For each environment variable is required to use `-e` prefix
```sh title:command
docker run --name <instance-name> -d -p <external-port:internal-port> -e <IMAGE-VARIABLE1=value> -e <IMAGE-VARIABLE2=value> <image-name|image-id>:<version>

# sample
docker run --name my-instance-name -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=sasa -e MYSQL_DATABASE=y-db mysql:8
```

### Attach instance
```sh title:command
docker attach <name|container-id>

docker attach my-instance-name
# or
docker attach aae2f44c8c19
```

### Show log
```sh title:command
docker logs <name|container-id>

# sample
docker logs my-instance-name
# or
docker logs aae2f44c8c19
```

#### Show log attached
```sh title:command
docker logs -f <name|container-id>

# sample
docker logs -f my-instance-name
# or
docker logs -f aae2f44c8c19
```

### Delete instance
- To delete some instances is required named with spaces
```sh title:command
docker rm <name|container-id> <name|container-id>

# sample
docker rm aae2f44c8c19 af8c0ab27b5b f64a00f44fa3
# or
docker rm my-instance-name1 my-instance-name2 my-instance-name3
```

#### Delete instance after stop it
```sh title:command
docker run -d -p <external-port:internal-port> --rm <image-name|image-id>:<version>

# sample
docker run -d -p 3306:3306 --rm mysql:8
```

#### Delete all instances
```sh title:command
docker container prune
```

### Inspect instance
```sh title:command
docker inspect <name|container-id>

# sample
docker inspect my-instance-name
# or
docker inspect aae2f44c8c19
```

### Restart instance automatically in failure case
```sh title:command
docker run -d -p <external-port:internal-port> --restart always <image-name|image-id>:<version>

# sample
docker run -d -p 3306:3306 --restart always mysql:8
```

### Process running inside the instance
```sh title:command
docker container top <name|container-id>

# sample
docker top my-instance-name
# or
docker top aae2f44c8c19
```

---
## Images

### List images
```sh title:command
docker images 
```

### Delete images 
```sh title:command
docker rmi [<name|container-id>]

# sample
docker rmi my-image-name
# or
docker rmi 7462b00f9003
```

### Delete all images 
```sh title:command
docker image prune
```

### Inspect images 
```sh title:command
docker image inspect <image-name|image-id>:<version>

# sample
docker image inspect my-image-name
# or
docker image inspect 7462b00f9003
```

---
## Inside docker
```sh title:command
docker exec -it <name|container-id> /bin/bash

# sample
docker exec -it my-instance-name /bin/bash
# or
docker exec -it aae2f44c8c19 /bin/bash
```

#### Run image and inside 
```sh title:command
docker run -p <external-port:internal-port> --rm -it <image-name|image-id>:<version> /bin/bash

# sampe
docker run -p 3306:3306 --rm -it mysql:8 /bin/bash
```

---
## Build instance
```sh title:command
docker build -t <instance-name>:<version> . 

# sample
docker build -t my-new-instance-name:1.0.0 . 
```

### Build instance specifying Dockerfile 
```sh title:command
docker build -t <instance-name>:<version> . -f </path/Dockerfile>

# sample
docker build -t my-new-instance-name:1.0.0 . -f ./my-folder/Dockerfile
```

---
## Copy files

### From local to instance
```sh title:command
docker cp </local/file.txt> <name|container-id>:</destination/path/inside/docker/file.txt>

# sample
docker cp ./my-folder/file.txt my-instance-name:/apps/file.txt
# or
docker cp ./my-folder/file.txt aae2f44c8c19:/apps/file.txt
```

### From instance to local
```sh title:command
docker cp <name|container-id>:</path/inside/docker/file.txt> </destination/local/file.txt>

# sample
docker cp my-instance-name:/apps/file.txt ./my-folder/file.txt
# or
docker cp aae2f44c8c19:/apps/file.txt ./my-folder/file.txt

```

---
## Network

### Create network
```sh title:command
docker network create <network-name>

# sample
docker network create my-network-name
```

### List networks
```sh title:command
docker network ls
```
#### Run instance with network
```sh title:command
docker run -d -p <external-port:internal-port> --rm --name <instance-name> --network <network-name> <image-name|image-id>:<version>

# sample
docker run -d -p 3306:3306 --name my-instance-name -e MYSQL_PASSWORD=12345 --network my-network-name mysql:8

```

### Inspect network
```sh title:command
docker network inspect <network-name>

# sample
docker network inspect my-network-name
```

### Attach network to existing instance
```sh title:command
docker network connect <network-name|network-id> <instance-name|container-id>

# sample
docker network connect my-network-name my-instance-name
# or
docker network connect 5850a9fe5422 aae2f44c8c19
```

### Detach network from instance
```sh title:command
docker network disconnect <network-name|network-id> <instance-name|container-id>

# sample
docker network disconnect my-network-name my-instance-name
# or
docker network disconnect 5850a9fe5422 aae2f44c8c19
```

---
## Volumes

### List volume
```sh title:command
docker volume ls
```

- Volume associate to a container
```sh title:command
docker ps -a --filter volume=<volume-name | volume-id>

# sample
docker ps -a --filter volume=3d762c2860e88d331bcbf79352f10edbdfe3e10632dc0f6a4374979431b0ab08
```

#### List orphan volumes
```sh title:command
docker volume ls -qf dangling=true
```

#### Delete all orphan volumes
```sh title:command
docker volume rm $(docker volume ls -qf dangling=true)
```

### Create volume
```sh title:command
docker volume create <volume-name>

# sample
docker volume create my-volume-name
```

### Mount volume
```sh
docker run -d -p <external-port:internal-port> --name <instance-name> --network <network-name> -v <volume-name>:</instance/docker/path> --restart always <image-name|image-id>:<version>

# sample
docker run -d -p 3306:3306 --name my-instance-name -e MYSQL_ROOT_PASSWORD=sasa --network my-network-name -v my-volume-name:/var/lib/mysql --restart always mysql:8
# or
docker run -d -p 3306:3306 --name my-instance-name -e MYSQL_ROOT_PASSWORD=sasa --network my-network-name -v /home/my-user/db:/var/lib/mysql --restart always mysql:8
```


## Backup

```sh title:'Stop containers'
docker ps -q | xargs docker stop
```

```sh title:'Export containers'
docker ps -a -q | xargs -I {} sh -c 'docker export -o container-{}.tar {}'
```

```sh title:'Backup images'
docker images -q | xargs -I {} sh -c 'docker save -o image-{}.tar {}'
```

```sh title:'Backup volumes'
docker volume ls -q | xargs -I {} sh -c 'docker run --rm -v {}:/volume -v $(pwd):/backup ubuntu tar cvf /backup/volume-{}.tar /volume'
```

