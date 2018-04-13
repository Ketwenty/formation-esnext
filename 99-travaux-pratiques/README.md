# Travaux Pratiques

## Objectifs
* Faire un tour d'horizon des nouveautés apportées par ES2015.


## Répertoire TP

* Créer un répertoire _/es2015_.

* Créer un script _/es2015/app.js_.

```
/es2015
    app.js
```

Le code sera écrit dans le fichier _/es2015/app.js_.

## let
* Créer une variable _favoriteCityId_  (à l'aide mot clé _let_) qui contient la chaîne de caractères : "rome".
* Afficher dans la console (_console.log(...)_) la variable _favoriteCityId_.
* Affecter une nouvelle valeur à la variable _favoriteCityId_ : une chaînes de caractères : "paris".
* Afficher dans la console (_console.log(...)_) la variable _favoriteCityId_.
* Vérifier le résultat dans la console

```
rome
paris
```

## const
* Créer une constante _citiesId_  (à l'aide mot clé _const_) qui contient un tableau de chaînes de caractères : "paris", "nyc", "rome", "rio-de-janeiro".
* Afficher dans la console (_console.log(...)_) la constante _citiesId_.
* Vérifier le résultat dans la console .
* Affecter une nouvelle valeur à la constante _citiesId_ : un tableau vide par exemple. Que constatez-vous dans la console ? Mettre en commentaire la ligne de code de la nouvelle affectation.
* Ajouter un nouvel élément au tableau : "tokyo".
* Afficher dans la console (_console.log(...)_) la constante _citiesId_.

```
["paris", "nyc", "rome", "rio-de-janeiro"]
["paris", "nyc", "rome", "rio-de-janeiro", "tokyo"]
```

## Création d'objet
* Créer une fonction _getWeather_ qui possède un paramètre _cityId_.
* Dans cette fonction, ajouter 2 variables locales :
    * _city_ qui stocke la valeur du paramètre _cityId_ en lettres majuscules.
    * _temperature_ valorisé à 20.
    * Utiliser la nouvelle syntaxe ES2015, pour retourner un objet de la forme _{city: "PARIS", temperature: 20}_.
* Créer une constante _weather_ qui exécute la fonction _getWeather_ en lui passant en paramètre _favoriteCityId_.
* Afficher dans la console constante _weather_

```
Object {city: "PARIS", temperature: 20}
```

## Affectation destructurée
* Avec la nouvelle syntaxe d'affectation destructurée, créer deux constantes _city_ et _temperature_ qui récupère leurs valeurs à partir de la constante _weather_.
* Afficher dans la console la valeur de constante _city_.
* Afficher dans la console la valeur de constante _temperature_.

```
PARIS
20
```

## Rest operator
* A l'aide du _rest operator_, créer à partir du tableau _citiesId_, 3 constantes : _parisId_, _nycId_ et _othersCitiesId_.
* Afficher dans la console la valeur de constante _parisId_.
* Afficher dans la console la valeur de constante _nycId_.
* Afficher dans la console la taille du tableau _othersCitiesId_.

```
paris
nyc
3
```

## Classe
* Créer une classe _Trip_.
* Ajouter un constructeur avec les propriétés : _id_, _name_, _imageUrl_.
* Créer un objet _parisTrip_ avec la classe _Trip_ avec les informations suivantes :
 * id : paris
 * name : Paris
 * imageUrl : img/paris.jpg
 * Afficher dans la console :
* * l'objet _parisTrip_.
* * la propriété _name_ de l'objet _parisTrip_.
* Vérifier le résultat dans la console.

```
Trip {id: "paris", name: "Paris", imageUrl: "img/paris.jpg"}
Paris
```

* Ajouter la méthode _toString()_ à la classe _Trip_ qui permet d'avoir l'affichage ci-après.
Afficher dans la console le résultat de son exécution sur l'objet _parisTrip_.

```
Trip [paris, Paris, img/paris.jpg]
```

* Ajouter un getter et un setter pour la propriété _price_.
La classe sauvegardera la valeur dans une variable privée appellée __price_.
* Compléter la méthode _toString()_ pour qu'elle affiche la valeur de __price_.
* Valoriser à _100_ la propriété _price_ de l'objet _parisTrip_.
* Afficher dans la console, le résultat de la méthode _toString()_ de l'objet _parisTrip_.

```
Trip [paris, Paris, img/paris.jpg, 100]
```

* Ajouter à la classe _Trip_ une méthode statique _getDefaultTrip()_ qui retourne une instance de la classe _Trip_ valorisée avec les informations suivantes :
 * id : rio-de-janeiro
 * name : Rio de Janeiro
 * imageUrl : img/rio-de-janeiro.jpg
* Créer une constante _defaultTrip_ qui récupère le résultat de l'exécution de la méthode _getDefaultTrip()_.
* Afficher dans la console _defaultTrip.toString()_.

```
Trip [rio-de-janeiro, Rio de Janeiro, img/rio-de-janeiro.jpg, undefined]
```

## Héritage
* Créer la classe _FreeTrip_ qui étends _Trip_.
* Elle se construit avec les informations suivantes : _id_, _name_ et _imageUrl_. La propriété _price_ est valorisé par défaut à 0.
* Créer une constante _freeTrip_, instance de la classe _FreeTrip_ avec les informations suivantes :
 * id : nantes
 * name : Nantes
 * imageUrl : img/nanges.jpg
* Afficher dans la console _freeTrip.toString()_

```
Trip [nantes, Nantes, img/nanges.jpg, 0]
```

* Redéfinir la méthode _toString()_ dont le résultat est la concaténation de la chaîne de caractères _Free_
et du résultat de l'exécution de la méthode _toString()_ de la classe _Trip_.

```
FreeTrip [nantes, Nantes, img/nanges.jpg, 0]
```

## Promise, Set, Map, Arrow Function

Partons de la base de code suivante :

```js
class TripService {

    constructor() {
        // TODO Set of 3 trips
        //
        // new Trip('paris', 'Paris', 'img/paris.jpg')
        // new Trip('nantes', 'Nantes', 'img/nantes.jpg')
        // new Trip('rio-de-janeiro', 'Rio de Janeiro', 'img/rio-de-janeiro.jpg')
    }

    findByName(tripName) {
        // TODO return promise
    }
}

class PriceService {

    constructor() {
        // TODO Map of 2 trips
        // 'paris' --> price = 100
        // 'rio-de-janeiro' --> price = 800)
        // no price for 'nantes'
    }

    findPriceByTripId(tripId) {
        // TODO return promise
    }
}
```

* Compléter le constructeur de la classe _TripService_ pour initialiser un Set de 3 objet _Trip_.

* Compléter le constructeur de la classe _PriceService_ pour initialiser une Map (clé = identifiant voyage, valeur = prix).
Stocker y 2 prix pour les villes _Paris_ et _Rio de Janeiro_.

* Compléter la méthode _findByName(tripName)_ pour qu'elle renvoie une promesse.
 * Pour simuler une récupération des données distantes, utiliser la méthode _setTimeout(fn,delay)_ pour créer une latence de 2s.
 * Renvoyer l'objet _Trip_ correspondant au nom du voyage en paramètre.
 * Si aucun voyage ne correspond au nom en paramètre, renvoyer une erreur _No trip with name xxx_.

* Compléter la méthode _findPriceByTripId_ pour qu'elle renvoie une promesse.
 * Utiliser la méthode _setTimeout(fn,delay)_ pour créer une latence de 2s.
 * Renvoyer la valeur du prix si trouvé
 * Si aucun prix trouvé, renvoyer l'erreur _No price found for id xxxx_.

* Créer une instance de _TripService_ et une instance de _PriceService_.
* Effectuer une recherche par nom de voyage avec la valeur _Paris_. Afficher dans la console le résultat trouvé.

```
Trip found : Trip {id: "paris", name: "Paris", imageUrl: "img/paris.jpg"}
```

* Effectuer une recherche par nom de voyage avec la valeur _Toulouse_. Afficher dans la console le résultat trouvé.

```
No trip with name Toulouse
```

* Chainer l'utilisation des services _TripService_ et _PriceService_ pour récupérer le prix du voyage _'Rio de Janeiro'_.

```
Price found : 800
```

* Chainer l'utilisation des services _TripService_ et _PriceService_ pour récupérer le prix du voyage _'Nantes'_.

```
No price for trip id nantes
```
