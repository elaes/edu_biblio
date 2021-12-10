# Moteur de recherche avec Elasticsearch

## Description

Moteur de recherche avec Elasticsearch.
Il permet de rechercher des mots dans une centaine de livres.
Le projet est en Vue.js/Node.js

## Schéma

- Elastic va indexer les livres
- Nginx sert la page en vueJS.
- La page en vueJS va se connecter au serveur node qui fournit une api vers elastic

```schema
                                       +--------+
                                       | vue.js |
                                       ++-------+
                                        |
+------------+               +-------------+
|            |               |  serveur |  |
|            <---------------------------  |
| navigateur |               |  nginx      |
|            |               +-------------+
|            |
|            |               +-----------+    +---------+
|            |               |  serveur  |    |         |
|            |               |           |    | elastic |     +--------+
|   vue.js   <--------------->  node.js  +<-------------------+ livres |
+------------+               +-----------+    +---------+     +--------+
```

## démarrage

Dans une console :

```shell
docker-compose up -d
```

laissez le temps à elasticsearch de démarrer puis taper dans une console :

```shell
docker exec gs-api "node" "server/load_data.js"
```

Les livres sont indexés. Vous pouvez tester sur http://localhost:8888/

## Liens utiles

- [le tuto du projet en Anglais](https://blog.patricktriest.com/text-search-docker-elasticsearch/)
- [la page github](https://github.com/triestpa/Guttenberg-Search)
