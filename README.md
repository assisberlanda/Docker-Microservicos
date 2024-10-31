# 🐳 Docker Microserviços
    minikube start

#### [Docker-Compose](https://github.com/docker/awesome-compose?tab=readme-ov-file)

### Criando um Cluster
    docker service create --name web-server --replicas 10 -p 80:80 httpd
    docker service ps web-server 
    docker node update --availability drain aws1
    docker service rm web-server

### Executando um contêiner
    docker pull ubuntu
    docker run ubuntu
    docker run ubuntu sleep 10
    docker run ubuntu sleep 1500
    docker stop [id]
    docker run --help
    docker run -it ubuntu
### ⚠️ Executando aplicações no contêiner
    docker run -dti  ubuntu 
    docker exec -it [id ou nome]  /bin/bash
### ⚙️ Excluindo e nomeando contêineres
    docker stop [id]
    docker rm [id]
    docker rmi [imagem]
    docker run -dti --name Ubuntu-A ubuntu
### Copiando arquivos para o contêiner
    docker exec -ti Ubuntu-A /bin/bash
    docker exec Ubuntu-A mkdir /destino/
    docker exec Ubuntu-A mkdir ls -l /
    nano Arquivo.txt
    docker cp arquivo.txt Ubuntu-A:/aula/
### Copiando arquivos do container
    docker cp Ubuntu-A:/destino/Meuzip.zip  Zipcopia.zip 
### Criando um contêiner do MySQL
    docker pull mysql 
    docker run -e MYSQL_ROOT_PASSWORD=Senha123 --name mysql-A -d -p 3306:3306 mysql
    docker exec -it mysql-A bash
    mysql -u root -p --protocol=tcp
## 🆑 Acessando um container externamente
    CREATE DATABASE aula;
    show databases;
    docker inspect mysql-A
## 🔥 Conectar banco de Dados Mysql
    mysql -u root -p --protocol=tcp
    Mysql -u root-p --protocol=tcp
## ✅ Banco de Dados
Posso conectar ao Banco de Dados, sem a necessidade de entrar dentro do meu contêiner, bastando instalar o mysql-client
#### no container
    Apt update
    Apt upgrade
    Apt install mysql-client
    Mysql -u root-p --protocol=tcp
### mudar o volume para persistências dos dados
    Docker run -v /hostdir:/containerdir mysql
    Docker volume create mysql_data
    Docer run mysql_data:/containerdir mysql
    docker run -e MYSQL_ROOT_PASSWORD=Senha123 --name mysql-A -d -p 3306:3306 --volume=/data:/var/lib/mysql mysql
    mysql -u root -p --protocol=tcp --port=3306
#### ****bind mount *****
    docker run -dti --mount type=bind,src=/opt/teste,dst=/teste debian
    docker run -dti --mount type=bind,src=/opt/teste,dst=/teste,ro debian
#### ***volumes****
    docker volume create teste
    docker volume ls
    /var/lib/docker/volumes/teste/_data	
    docker run -dti --mount type=volume,src=teste,dst=teste debian
    docker run  --name apache-A -d -p 80:80 --volume=/data/apache-A:/usr/local/apache2/htdocs/ httpd
    docker run  --name php-A -d -p 8080:80 --volume=/data/php-A:/var/www/html php:7.4-apache

#
🌎☁️🧩📌❇️💡❗️🆑✅🔗⌨️🔴☑️🔗🐳🔥🚀🚧🚦⚙️⚠️🌐✨
