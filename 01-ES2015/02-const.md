# const

Le mot clé `const` permet de créer des constantes.

```js
const PI = 3.14
PI = 12 // Uncaught TypeError: Assignment to constant variable.
```

Il est possible de modifier les propriétés d’une constante.

```js

const OBJ = {};
OBJ.nom = "NOM";
console.log(OBJ); // Object {nom: "NOM"}
```