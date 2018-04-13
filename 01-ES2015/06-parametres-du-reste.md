# Paramètre du reste (rest operator)


## Problématique
En JavaScript, il est toujours possible de passer le nombre d'arguments souhaités à une fonction.

Les différentes valeurs peuvent être récupérées via une variable spéciale`arguments`.

`arguments` n'est pas un véritable tableau (pas de méthode `forEach` par exemple) .

```js
function afficher(value) {
    for (var i=0; i< arguments.length; i++) {
        console.log(arguments[i]);
    }
}

afficher('Robert', 'Julien', 'Jean');
// Robert
// Julien
// Jean

```

## Syntaxe ES2015

ES2015 apporte une nouvelle syntaxe.

```js
function afficher(...values) {

    // values est un véritable tableau
    // elle possède la méthode forEach
    values.forEach(function(val){
        console.log(val);
    });
}
afficher('Robert', 'Julien', 'Jean');
// Robert
// Julien
// Jean
```

Le paramètre du reste peut s'associer à une affectation déstructurée.


```js
let tab = [10,20,30,40,50];
let [maValeur, ...leResteDesValeurs] = tab;
console.log(maValeur); // 10
console.log(leResteDesValeurs); // [20, 30, 40, 50]
```
