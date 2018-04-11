# Affectation destructurée

L'affectation destructurée est un raccourci permettant d'affecter des variables à partir d'objets.

```js
// soit un objet p1
let p1 = {  nom: 'Robert', prenom: 'Julien' };

// extraction des valeurs de l'objet p1
// dans des variables *nomPersonne* et *prenomPersonne*.
let {
    nom: nomPersonne,
    prenom: prenomPersonne
} = p1;

console.log(nomPersonne); // Robert
console.log(prenomPersonne); // Julien
```

Si les variables portent les mêmes noms que les propriétés, il est possible de faire plus concis.


```js
let p1 = {
    nom: 'Robert',
    prenom: 'Julien'
};

let { nom, prenom } = p1;

console.log(nom); // Robert
console.log(prenom); // Julien

```

Pour récupérer les valeurs des objets imbriqués.

```js
let p1 = {
    nom: 'Robert',
    prenom: 'Julien',
    adresse : {
        numero : 2,
        rue: 'Angular',
        ville: 'Nantes'
    }
};

let { adresse: { ville } } = p1;

console.log(ville); // Nantes
console.log(adresse); // ReferenceError: adresse is not defined
```

L'affectation destructurée fonctionne aussi avec des tableaux.

```js
let tab = [10,20,30,40,50];
let [maValeur, maSecondeValeur] = tab;

console.log(maValeur); // 10
console.log(maSecondeValeur); // 20

```

Combiné avec le raccourci de création d’objet, cela donne :

```js
function buildPersonne() {
    let nom = 'Robert';
    let prenom = "Julien";
    return { nom, prenom };
}

let { prenom } = buildPersonne();

console.log(prenom); // Julien
```