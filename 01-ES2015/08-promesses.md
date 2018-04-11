# Promesses

Les promesses ont pour objectif de simplifier la programmation asynchrone.

Elles permettent d'éviter l'enfer des callbacks.

## Problématique des callbacks

Soit l'exemple suivant :

```js
function getId(email, callback) {

    request('http://rechercherid?email='+email, {}, function(err, id) {
        callback(id);
    });
}

function getInfos(id, callback) {

    request('http://rechercherinfo?id='+id, {}, function(err, infos) {
        callback(infos); // exemple d'infos {nom: 'Robert', token: 'AXX'};
    });

}

function getSecrets(token, callback) {

    request('http://recherchersecret?token='+token, {}, function(err, secret) {
             callback(secret)
    });

}
```
A l'utilisation cela donne :

```js
getId('a@a.fr', function (id) {
    getInfos(id, function (infos) {
        getSecrets(infos.token, function (leSecret) {

            // problème 1 => j'ai accès à tout le contexte
            //  id, infos, secret

            // problème 2 => aucun mécanisme de traitement des erreurs
            // Ici j'ai le secret ou une erreur ???

            // problème 3 => le code devient de moins en moins lisible
            console.log(leSecret);
        });
    })
});

```

## Promesse

Une promesse se crée via la classe `Promise`.

Elle attend en paramètre une fonction avec deux paramètres : 

* `resolve` (cas sans erreur)
* `reject` (en cas d'erreur).

L'intérêt d'une promesse est qu'elle permet de chainer des opérations via sa méthode `then` et surtout de bien séparer les cas nominaux des cas d'erreur.

Exemple de transformation d'un code `callback`

```js
function getId(email) {

    // la méthode retourne un objet promesse
    return new Promise(function (resolve, reject) {

            request('http://rechercherid?email='+email, {}, function(err, id) {
                // callback(id); plus d'utilisation de callback

                // gestion des erreurs
                if(err) {
                    reject(err); // en cas d'erreur
                } else {
                    resolve(id); // en cas de succès
                }
            });

        });
}

```

La méthode `getId` peut s'utiliser comme suit :

```js
getId('a@a.fr')
    .then(function(id){
        // cas resolve
        }, function(error){
        // cas reject
        }
    );
```

La méthode `then` vient de l'objet `Promise`.

L'enchainement des promesses apporte un confort de lecture.

Exemple sans gestion d'erreurs.

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
    });

```

Exemple avec gestion des cas d'erreurs pour chaque promesse.

```js
getId('a@a.fr')
.then(function (id) {
        return getInfos(id);
    }, function (erreur) {
        // gestion erreur getId
        // return erreur; => continuer l'enchainement des promesses
    })
.then(function (infos) {
    return getSecrets(infos.token);
    }, function (erreur) {
        // gestion erreur getInfos
    })
.then(function (secret) {
    console.log(secret);
    }, function (erreur) {
    // gestion erreur getSecrets
    });
```

Exemple gestion globale des erreurs.

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
