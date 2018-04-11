# Modules

Le mot clé `export` rend disponible un élément à l'extérieur d'un fichier.

Soit la structure suivante :

```
/dossier
    person.js
    main.js
```

Objectif : utiliser un élément du fichier `person.js` dans le fichier `main.js`.

## `export`

Export de fonctions dans le fichier `person.js`.

```js
// Fichier person.js
let ditQuelqueChose = (debutPhrase, nom, prenom) => {
    return `${debutPhrase} ${prenom} ${nom}`;
};
export function getBonjour(nom, prenom) {
    return ditQuelqueChose('Bonjour', nom, prenom);
}
export function getAurevoir() {
    return ditQuelqueChose('Aurevoir', nom, prenom);
}
```

## `import`

Utilisation dans le fichier `main.js`.
Le mot clé `import` permet d'importer un élément d'un module extérieur.

```js
// Fichier main.js
import { getBonjour, getAurevoir } from 'person';

console.log(getBonjour('Robert', 'Julien'));
console.log(getAurevoir('Robert', 'Julien'));
```

Il est possible d'importer une partie d'un module. Et même de définir un alias.

```js
// Fichier main.js
import {getBonjour as bonj} from 'person';

console.log(bonj('Robert', 'Julien'));
```

Importer toutes les éléments d'un module.

```js
import * as bonj from 'person';

console.log(bonj.getBonjour('Robert', 'Julien'));
```

## `default`

Si le module n'expose qu'une seule fonction ou valeur ou classe, il est possible d'utiliser le mot clé `default`.

Dans ce cas, il n'y pas d'accolade lors de l'import.

Exemple de fichier `person.js` :


```js
// fichier person.js
export default class Person {

}
```

Exemple de fichier `main.js` :

```js
// fichier module.js
// noter l'absence d'accolades
import Person from 'person';

let p = new Person();
```