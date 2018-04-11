# Map

* Dictionnaire (structure à clé-valeur).

```js
let p1 = {nom: 'Robert', prenom: 'Julien'};
let p2 = {nom: 'Emilie', prenom: 'Julie'};

// créer
let persons = new Map();

// alimenter
persons.set(1, p1);
persons.set(2, p2);

// utiliser
console.log(persons.has(1)); // true
console.log(persons.get(1)); // p1
console.log(persons.size); // 2
persons.delete(2);
console.log(persons.size); // 1

```