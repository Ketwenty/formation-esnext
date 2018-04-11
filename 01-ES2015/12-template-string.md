# Template de String

* Utiliser l'accent grave (`) pour créer une chaine de caractère dynamique.

* Il est possible d'invoquer une fonction dans un template de String.

```js
let nom = 'Robert';
let prenom = 'Julien';
let oldHello = 'Bonjour ' + nom + ' ' + prenom;
let newHello = `Bonjour ${nom} ${prenom}`;

console.log(newHello);

function getFullname() {
    return nom + ' ' + prenom;
}

let anotherHello = `Bonjour ${getFullname()}`;
console.log(anotherHello);
```

* Support du multilignes.  L'indentation, les sauts de ligne sont conservés.

```js
let nom = 'Robert';
let prenom = 'Julien';

let newHello = `Bonjour ${nom} ${prenom},
Ceci est une lettre de motivation.
Elle contient plusieurs lignes.
    Et une signature.
`;
console.log(newHello);
```

