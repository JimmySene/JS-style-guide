# JS Style Guide

## Commentaires

Utiliser la syntaxe *//* suivi d'un espace.  
Le commentaire doit toujours se situer juste au dessus du code commenté.

```js
// Ceci est un commentaire sur le console.log
console.log("Le commentaire du dessus me concerne !");
```

## Nommage des variables, fonctions...

Casing : **camelCase**.  
Noms clairs, éviter les abréviations et les noms trops longs.  
Nommer ses variables d'incrément i ou j dans les boucles est OK (convention).

## Chaines de caractères

Privilégier les simples quotes aux doubles quotes.

```js
const name = 'J.S';
```

Dès qu'il y a une variable à insérer dans la chaine, utiliser les littéraux de gabarits.

```js
const superString = `Ma super chaine en ${langageName}`;
```

## Blocs de code (fonctions, conditions, boucles...)

Privilégier la syntaxe étendue à la syntaxe sur une seule ligne.  
Faire débuter le bloc de code sur la première ligne. Finir le bloc de code sur une nouvelle ligne.  
Dans le bloc de code, une seule instruction par ligne. Les instructions doivent toutes finir par un ;  
Pas d'espace entre le nom d'une fonction / le mot clef if / while / for et la paire de parenthèses.  
Pas d'espace entre la paire de parenthèses et ce qu'il y a dedans.  
Espace entre les paramètres.

```js
function superFonction(machin, truc) {
  console.log('Ma super fonction !');
}
```

Espaces entre les opérateurs et les opérandes.

```js
if(age >= 18 && espece === 'humain') {
  console.log('Il est majeur !');
}
```

## Déclaration des variables

Utiliser les mots clés *let* ou *const*, pas *var*.

```js
// utiliser let si la valeur est amenée à être modifiée
let score = 40;
score += 2;

// utiliser const si la valeur reste fixe
const gameName = 'Super jeu';
```

## Conditions

Pour tester une égalité, privilégier l'égalité stricte.

```js
// on privilégie === au ==
if(email === 'labonneadresseemail@gmail.com') {
  // ...
}
```

Si il y a un test sur une valeur booléenne, privilégier l'utilisation du raccourci.

```js
// on privilégie l'utilisation du raccourci au lieu de === true / false
if(isMajor) {
  // ...
}
```

En cas d'une condition switch formater comme suit :

```js
switch(panier) {
  case 'Bananes':
    console.log('...');
    break;
  case 'Citrons':
    console.log('...');
    break;
  default:
    console.log('...');
}
```

## Ternaires

Les ternaires doivent être écrites sur une seule ligne.

```js
const statut = (age >= 18) 'majeur' : 'mineur';
```

## Boucles

L'itérateur dans une boucle for doit être déclarée avec le mot clef *let*.

```js
for(let i = 0; i < 10; i++) {
  // ...
}
```

## Fonctions

Utiliser le mot clef *function* sans stocker la fonction dans une variable.

```js
// ça c'est recommandé
function sum(a, b) {
  return a + b;
}
// ça c'est pas recommandé
const sum = function(a, b) {
  return a + b;
}
```

Pour les fonctions anonymes de callback, privilégier la syntaxe fléchée.

```js
const truc = array.find((elem) => elem === 'surprise');
```

## Tableaux

Utiliser la syntaxe littérale, pas *new Array(length)*.

```js
const array = [
  'elem1',
  'elem2',
  // ...
]
```

Utiliser la méthode *push()* pour insérer un élément dans un tableau.

## Objets

### Objets Natifs

Utiliser la syntaxe littérale, pas *new Object()*.

```js
const obj = { 
  prop: 'valeur',
  prop2: 'valeur',
  // +
  ...
}
```

### POO

Les noms de classes doivent commencer par une majuscule.  
Espace entre le nom de la classe et le début du bloc de code.

```js
class Pizza {

}
```
