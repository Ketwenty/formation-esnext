# Générateurs

Un générateur est un fonction qu'il est possible de quitter puis reprendre.
Le contexte de la fonction est sauvegardé entre les reprises.

Il se déclare avec le mot clé `function*`.

Le mot clé `yield` permet de publier une valeur.



```js
function* creerID(){
  var index = 0;
  while(index < 3){
    yield index++;
  }
}

// gen est un objet Generator.
// il possède les méthodes suivantes :
// * next() : récupère la valeur publiée par yield
// * return(): récupère la valeur publiée et termine le générateur
// * throw() : lève une exception et termine le générateur
var gen = creerID();

console.log(gen.next().value); // 0
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
console.log(gen.next().value); // undefined
```

Pour aller plus loin :

* https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Instructions/function*.
* Objet Generator : https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Generator

