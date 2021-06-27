# TP DOCKER - JOOMLA

Ce TP a pour objectif de construire des conteneurs Docker afin de faire fonctionner l'application [__Joomla__](https://www.joomla.fr/).

-----------

## Comment tout cela fonctionne ?
Dans le répertoire /joomla se trouve un Dockerfile. A l'intérieur de ce fichier se trouve l'ensemble des commandes permettant de monter l'image qui fera fonctionner le service Joomla. Ce conteneur contiendra ainsi : PHP, NGINX et JOOMLA.  
Dans un second répertoire nommé /joomla_db se trouve les variables d'environnement MYSQL (qu'il faut remplir à partir du fichier .env-template, puis supprimer le terme "-template) permettant à Joomla de se connecter au conteneur de la base de données MARIADB. Ce deuxième conteneur est créé à partir du fichier "docker-compose".  

Dans le fichier "joomla.local.conf" se trouve la configuration du serveur NGINX pour pouvoir accéder au service Joomla. Il faut penser à bien modifier l'adresse IP du "server-name".  

En exécutant le fichier "docker-compose" via la commande : `docker-compose up --build`, les deux conteneurs JOOMLA et MARIADB vont se monter, ainsi que tout les éléments de configuration autour de ceux-ci. Un volume persistant sera créé et monté pour la base de données MARIADB et les deux conteneurs seront dans le même réseau.  

Une fois le tout monté, le service Joomla sera accessible via une page web en tapant l'adresse IP du serveur sur lequel le service est installé. Il ne reste plus qu'a tout configuré !  

-----------

__Quelques commandes Docker :__  
`docker ps -a` > afficher les conteneurs  
`docker image ls` > afficher les images  
`docker volume ls` > afficher les volumes  
`docker build -t [NOM_IMAGE] -f [CHEMIN_DOCKERFILE] .` > créé une image Docker à partir d'un Dockerfile  
`docker-compose up --build` > monter plusieurs conteneurs, volumes et réseaux à partir d'un fichier docker-compose  
`docker-compose down` > démonter tout les services du docker-compose  
