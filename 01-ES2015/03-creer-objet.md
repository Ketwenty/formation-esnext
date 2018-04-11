# Création des objets

Un nouveau raccourci pour créer des objets quand la propriété de l’objet à le même nom que la variable utilisée.

Prenons l'exemple ci-dessous :

```js
function buildPersonne() {
    let nom = 'Robert';
    let prenom = 'Julien';
    return { nom: nom, prenom: prenom};
}
```

L'utilisation de la nouvelle syntaxe donnerait :

```js
function buildPersonne() {
    let nom = 'Robert';
    let prenom = 'Julien';
    return { nom, prenom}; // équivalent de { nom: nom, prenom: prenom}
}
```

Cette notation fonctionne avec les mots clés : `var`, `let` et `const`.

```js
let nom = 'Robert';
let prenom = 'Julien';

const obj = { nom, prenom };
```