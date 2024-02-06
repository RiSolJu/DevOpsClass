# TP Part 1 : Docker

## 1-1 Document your database container essentials: commands and Dockerfile.

Pour build : docker build -t quentinles/myfirstapp .  

- docker run -p "8090:8080" --net=app-network --name=adminer -d adminer
&
- docker run -e POSTGRES_PASSWORD=pwd --net=app-network -v data-postgres:/var/lib/postgresql/data --name myapp quentinles/myfirstapp

I used two dockers on the same network "app-network" for them to communicate. The password of Postgres is an environment variable given by the cmd command.

## 1-2 Why do we need a multistage build ?

We use multistage build to create smaller images and to make them more efficient. 
They can copy "artifacts" from previous stages, making in to possible to keep only what's necessary at each step of the run time.

## 1-3 Document docker-compose most important commands. 

- **docker-compose up -d** : Pour lancer le fichier docker-compose.yml dans le dossier courant
- **docker-compose down** : Pour stopper tous les dockers correspondant au dossier courant
- **docker-compose logs -f** : Affiche les logs et suis les prochains logs qui vont arriver. 
- **docker-compose ps** : Affiche des infos relatives aux docker enfant du docker-compose du dossier courant.

## 1-4 Document your docker-compose file.

Done.

## 1-5 Commands :

docker tag backend quentinles/backend:1.1
docker push quentinles/backend:1.1 

## 2-1 What are testcontainers?

This is a way to test docker containers and to run them while testing them.


