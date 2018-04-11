# Set

* Représente un ensemble d'éléments.

* Ignore les doublons.

* Plusieurs propriétés/méthodes : `add`, `size`, `has`, ...


```js
let p1 = {nom: 'Robert', prenom: 'Julien'};
let p2 = {nom: 'Emilie', prenom: 'Julie'};

let persons = new Set();
persons.add(p1);
persons.add(p2);

console.log(persons.size); // 2
console.log(persons.has(p1)); // true

persons.add(p1);
console.log(persons.size); // 2

persons.delete(p1);
console.log(persons.size); // 1
```