FROM postgres:14.1-alpine

# Option pour la mise en place du postgres, le "$" indique une variable d'environnement 
ENV POSTGRES_DB=$POSTGRES_DB \
   POSTGRES_USER=$POSTGRES_USER \
   POSTGRES_PASSWORD=$POSTGRES_PASSWORD

# Copie des scripts SQL dans le container pour initialiser la DB
COPY CreateScheme.sql /docker-entrypoint-initdb.d/
COPY InsertData.sql /docker-entrypoint-initdb.d/

