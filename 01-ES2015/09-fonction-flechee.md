# Fonction fléchée

La fonction fléchée `=>` JavaScript propose 2 éléments :

* un raccourci d'écriture pour les fonctions anonymes (souvent utilisée dans du code asynchrone)
* une fonction qui ne possède pas ses propres valeurs de `this`, `arguments`, `super` et `new.target`.

Le code suivant :

```js
getId('a@a.fr')
    .then(function (id) {
        return getInfos(id);
    })
    .then(function (infos) {
        return getSecrets(infos.token);
    })
    .then(function (secret) {
        console.log(secret);
    })
    .catch(function(error){
        // gestion globale des erreurs
    });
```

pourrait s'écrire :

```js
getId('a@a.fr')
    // pas besoin de return s'il n'y a qu'une seule ligne de code
    .then(id => getInfos(id))
    .then(infos => getSecrets(infos.token))
    .then(secret => console.log(secret))
    .catch(error => {
    // Si plusieurs lignes de code
    });
```