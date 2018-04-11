# `let`

## Problématique du mot clé `var`


```js
function getNomCompletAvecVar(sexe) {
        if(sexe == 'M') {
            var nomComplet = 'Robert';
        }
        console.log(nomComplet); // affiche Robert
    }
getNomCompletAvecVar('M');
```

En javascript, il y a le concept de **hoisting** (remontée) qui déclare la variable en début de fonction.
La portée d'une variable déclarée avec `var` est la fonction et non le bloc de code.

## Mot clé `let`

* L'accès à une variable peut désormais être restreint à son bloc grace au mot clé `let`.

* `let` a été pensé pour remplacer définitivement `var` à long terme.

```js
function getNomCompletAvecLet(sexe) {
    if(sexe == 'M') {
        let nomComplet = 'Robert';
    }
    console.log(nomComplet); // Uncaught ReferenceError: nomComplet is not defined
}
```