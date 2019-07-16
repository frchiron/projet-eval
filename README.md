# Evaluation

Le projet consiste à créer une application Spring Boot from scratch.

Un README.md doit être fourni, il doit indiquer :
- les pré-requis nécessaires
- comment lancer l'application
- des exemples pour tester l'application
- les choix éventuels d'implémentation si besoin

L'ensemble du projet du être fourni sous forme de zip. Il n'est pas utile de fournir le répertoire /target.

- Créer une application Spring Boot
- L'application doit disposer d'un contrôleur REST avec les points d'entrée suivants :
  - `GET /book?title=<monTitre>` 
      => lecture de l'enregistrement Book avec comme title = `<monTitre>`
      
      Exemple 
  ```
  GET /book?title=Faber
  =>
  {
     'id' : '1',
     'title' : 'Faber',
     'author' : 'Garcia',
     'year' : '2013'
  }
  ```
  - `GET /book`

      => lecture de l'ensemble des enregistrements Book
  
      Exemple 
  ```
  GET /book
    =>
    [ {
        'id' : '1',
        'title' : 'Faber',
        'author' : 'Garcia',
        'year' : '2013'
    },
    ...
    ]
  ```
  
  
  - `POST /book`
 
      => création d'un enregistrement Book avec les champs suivants : title (chaîne de caractères sans espace), author (chaîne de caractères sans espace), year (date au format <YYYY>)
 
     Exemple 
 ```
  POST /book
  { 'title' : 'monTitre',
     'author' : 'monAuteur',
     'year' : '2019'
     }
  => Retour de l'id généré (avec si possible un code HTTP 201)
   2  
 ```
 
- L'application doit stocker l'ensemble des enregistrements dans une base de données H2 embarquée, via Spring JPA  


NOTES : 
- pour des raisons de simplicité on prendra l'hypothèse que les champs des enregistrements ne contiennent pas d'espace. En particulier un author sera désigné par un nom sans espace
- la réalisation du point d'entrée POST /book, plus complexe, doit s'effectuer dans un 2nd temps. Dans un 1er temps, pour valider le bon fonctionnement des points d'entrée GET, en créant temporairement un point d'entrée `GET /bookexample` qui génère des enregistrements Book
