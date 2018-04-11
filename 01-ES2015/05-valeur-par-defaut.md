# Valeur par défaut

Avant ES6, il y avait un pattern.

```js
function getNomComplet(nom, prenom) {
    let lastname = nom || 'INCONNU';
    let firstname = prenom || 'INCONNU';
    return lastname + ' ' + firstname;
}

getNomComplet(); // INCONNU INCONNU
getNomComplet('Robert'); // Robert INCONNU
getNomComplet('Robert', 'Julien'); // Robert Julien
```

Voici la syntaxe ES2015.

```js
function getNomComplet(
    nom = 'INCONNU', // utilisation de l'opérateur =
    prenom = 'INCONNU') {
    return nom + ' ' + prenom;
}
getNomComplet(); // INCONNU INCONNU
getNomComplet('Robert'); // Robert INCONNU
getNomComplet('Robert', 'Julien'); // Robert Julien
```

La valeur par défaut peut être définie via l'invocation d'une fonction.


```js
// fonction qui retourne une valeur par défaut.
function getDefault() {
    return 'INCONNU';
}

function getNomComplet(
    nom = getDefault(),
    prenom = getDefault()) {
    return nom + ' ' + prenom;
}

```