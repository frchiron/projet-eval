# Evaluation

Le projet consiste à créer une application Spring Boot from scatch.

Un README.md doit être fourni, il doit indiquer :
- les pré-requis nécessaires
- comment lancer l'application
- des exemples pour tester l'application
- les choix éventuels d'implémentation si besoin

L'ensemble du projet du être fourni sous forme de zip. Il n'est pas utile de fournir le répertoire /target.


- Créer une application Spring Boot
- L'application doit disposer d'un contrôleur REST avec les points d'entrée suivants :
  - GET /book?title=<monTitre 
      => lecture de l'enregistrement Book avec comme title = <monTitre>
      Exemple 
  ```
  GET /book?title=Carton jaune
  ```
  - GET /book
      => lecture de l'ensemble des enregistrements Book
  - POST /book
      => création d'un enregistrement Book avec les champs suivants : title, author, year, category
- L'application doit stocker l'ensemble des enregistrements dans une base de données H2 embarquée, via Spring JPA  
