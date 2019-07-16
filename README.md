# Evaluation

Le projet consiste à créer une application Spring Boot from scratch.

Un README.md doit être fourni, il doit indiquer :
- les pré-requis nécessaires
- comment lancer l'application
- des exemples pour tester l'application
- les choix éventuels d'implémentation si besoin

L'ensemble du projet doit être fourni sous forme de zip. Il n'est pas utile de fournir le répertoire /target.

- Créer une application Spring Boot avec les starters Web et data-jpa. S'appuyer sur le site https://start.spring.io/ pour générer votre squelette de projet Maven 

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
    {
        'id' : '2',
        'title' : 'Mon titre',
        'author' : 'mon auteur',
        'year' : '2019'
    }
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
 
- L'application doit stocker l'ensemble des enregistrements dans une base de données H2 embarquée, via Spring JPA. Pour rappel il faut rajouter la dépendance h2 pour utiliser cette base :

```
		<dependency>
			<groupId>com.h2database</groupId>
			<artifactId>h2</artifactId>
			<scope>runtime</scope>
		</dependency>
```


NOTES : 
- pour des raisons de simplicité on prendra l'hypothèse que les champs des enregistrements ne contiennent pas d'espace. En particulier un author sera désigné par un nom sans espace
- Help pour éviter de mettre en place JPA dès le début : on peut dans un 1er temps créer dans le Controller une liste de Book :
```
    private List<Book> books = Arrays.asList(new Book(....),new Book(..));

```

- la réalisation du point d'entrée POST /book, plus complexe, pourra s'effectuer dans un 2nd temps. Dans un 1er temps, pour valider le bon fonctionnement des points d'entrée GET, on peut créer temporairement un point d'entrée `GET /bookexample` qui génère des enregistrements Book
 - Help pour la création du POST :
 
 ```
     @PostMapping("/response")
    @ResponseBody
    public Long Book createBook(
      @RequestBody Book book) {
        // TODO
     }
``` 
