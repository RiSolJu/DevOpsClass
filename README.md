# TP Part 1 : Docker

## 1-1 Document your database container essentials: commands and Dockerfile.

Pour build : docker build -t quentinles/myfirstapp .  

- docker run -p "8090:8080" --net=app-network --name=adminer -d adminer
&
- docker run -e POSTGRES_PASSWORD=pwd --net=app-network -v data-postgres:/var/lib/postgresql/data --name myapp quentinles/myfirstapp

- docker ps -a : Pour afficher les dockers en marche ou exit

- docker image ls : Pour afficher les images docker en local

Et bien d'autres commandes pour supprimer des Images, des dockers etc.

I used two dockers on the same network "app-network" for them to communicate. The password of Postgres is an environment variable given by the cmd command.

In a DockerFile : 
- "From ****" is used to specify the docker image to use.
- "ENV ***" is used to specify environment variables
- "CP ***" is used to Copy a file inside the Docker after initialisation.

And the Docker file is commented.

## 1-2 Why do we need a multistage build ?

We use multistage build to create smaller images and to make them more efficient. 
They can copy "artifacts" from previous stages, making in to possible to keep only what's necessary at each step of the run time.

## 1-3 Document docker-compose most important commands. 

- **docker-compose up -d** : Pour lancer le fichier docker-compose.yml dans le dossier courant
- **docker-compose down** : Pour stopper tous les dockers correspondant au dossier courant
- **docker-compose logs -f** : Affiche les logs et suis les prochains logs qui vont arriver. 
- **docker-compose ps** : Affiche des infos relatives aux docker enfant du docker-compose du dossier courant.

## 1-4 Document your docker-compose file.

Le docker-compose récupère les Images docker sur le docker Hub puis déploie le Backend, database, proxy et le front. 
Il créé aussi un network permettant la communication entre les différents docker et un volume pour la bd.

## 1-5 Document your publication commands and published images in dockerhub.

docker tag backend quentinles/backend:1.1 : 

Cette commande étiquette l'image Docker nommée "backend" avec le tag "quentinles/backend:1.1". Cela signifie que nous prenons l'image "backend" existante et lui attribuons une nouvelle identité en lui donnant un nouveau nom (quentinles/backend) et une nouvelle version (1.1).

docker push quentinles/backend:1.1 : 

Cette commande pousse l'image Docker étiquetée (quentinles/backend:1.1) vers Docker Hub. Cela la rend accessible publiquement pour toute personne ayant les autorisations nécessaires pour accéder à ce référentiel sur Docker Hub.

# TP 3 - Github Actions

## 2-1 What are testcontainers?

Its a Java librairies which is used to test docker containers and to run them while testing them.

## 2-2 Document your Github Actions configurations.

Nos Workflows se lance comme ceci : 

Lors d'un push sur la branche Main ou Develop, on lance un test du Backend.
Si ce push était sur le Main et qu'il est completed et en succès, alors, le build and push sur le docker hub se lance.
Pour finir, le deploy se lance pour déployer le code sur les serveurs de production.

## 2-3 Document your quality gate configuration.

Done.

# TP 3 - Discover Ansible

## 3-1 Document your inventory and base commands

Done.

## 3-2 Document your playbook

Done.

## 3-3 Document your docker_container tasks configuration.



