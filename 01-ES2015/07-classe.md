# Classe

## Définir une classe

Le mot clé `class` permet de créer une classe.

La méthode `constructor` définit le constructeur de la classe.

Il est possible de définir dynamiquement des champs.

Le mot clé `this` définit les champs d’une classe.

```js
class Personne {
    constructor(nom,prenom) {
        this.nom = nom;
        this.prenom = prenom;
    }
}

let robert = new Personne('Oddet','Rossi');

console.log(robert.nom); // Oddet
console.log(robert.prenom); // Rossi

// Définition dynamique
robert.sexe = 'M';
```

## Définir une méthode

Une méthode se définit comme une fonction sans le mot clé function.

Les propriétés sont référencés via le mot clé `this`.

```js
class Personne {

    constructor(nom,prenom) {
        this.nom = nom;
        this.prenom = prenom;
    }

    getFullname() {
        return this.prenom + ' ' + this.nom;
    }
}

let robert = new Personne('Oddet','Rossi');

console.log(robert.getFullname()); // Rossi Oddet
```

## Getter / Setter

Les mots clé `get` et `set` permettent de définir des accesseurs pour une propriété.

Le mot clé this permet de référencer la propriété exposée.

Pas de visibilité privée pour les champs d’une classe.


```js
class Personne {

    constructor(nom,prenom) {
        this.nom = nom;
        this.prenom = prenom;
    }

    get age(){
        return this._age;
    }

    set age(newAge) {
        this._age = newAge;
    }
}

let robert = new Personne('Oddet','Robert');
robert.age = 12; // set age 12
console.log(robert.age); // get age

```

## Mot clé `static`

```js
class Personne {
    constructor(nom, prenom) {
        this.nom = nom;
        this.prenom = prenom;
    }

    // création d'une méthode static
    static getDefaultCivilite() {
        return 'Mademoiselle';
    }
}
console.log(Personne.getDefaultCivilite()); // Mademoiselle
```

## Héritage

### `extends`

Le mot clé `extends` permet de définir une relation d’héritage entre deux classes.

```js
class Personne {
    constructor(nom, prenom) {
        this.nom = nom;
        this.prenom = prenom;
    }
}

class Client extends Personne {
}

let c = new Client(); // Client {nom: undefined, prenom: undefined}
```

### `super`

Le mot clé `super` permet de référencer des éléments de la classe parente.

```js
class Personne {
    constructor(nom, prenom) {
        this.nom = nom;
        this.prenom = prenom;
    }
}

class Client extends Personne {
    constructor(nom, prenom, matricule) {
        super(nom, prenom);
        this.matricule = matricule;
    }
}

let c = new Client('Ro','Jul','A01'); // Client {nom: "Ro", prenom: "Jul", matricule: "A01"}
```

### Redéfinition des méthodes

Il est possible de redéfinir une méthode.

Voici un exemple ici `getNomComplet`.

```js
class Personne {
    constructor(nom, prenom) {
        this.nom = nom;
        this.prenom = prenom;
    }
}
```

```js
class Personne {
    constructor(nom, prenom) {
        this.nom = nom;
        this.prenom = prenom;
    }

    getNomComplet() {
        return this.nom + ' ' + this.prenom;
    }
}

class Client extends Personne {
    constructor(nom, prenom, matricule) {
        super(nom, prenom);
        this.matricule = matricule;
    }

    // redéfinition de méthode
    getNomComplet() {
        return super.getNomComplet() + ' ' + this.matricule;
    }
}

let c = new Client('Ro','Jul','A01'); // Client {nom: "Ro", prenom: "Jul", matricule: "A01"}

console.log(c.getNomComplet()); // Ro Jul A01

```

