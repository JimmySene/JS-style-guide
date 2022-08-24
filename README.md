# Simple JS Style Guide

**Comment écrire proprement du code JavaScript ?**

Voilà qui pourrait faire naître un débat aussi intense qu'el famoso **Pain au chocolat VS Chocolatine** ! 😲

J'exagère ? Sans doute un peu.

Mais force est de reconnaitre que certaines règles du clean code JS semblent plebiscitées par tous, quand d'autres au contraire semblent parfois se contredires... 🙄

L'idée de ce guide est de vous aider à y voir plus clair. Je l'ai conçu en ayant à l'esprit de toujours garder l'essentiel, tout en enlevant le superflu pour en faire un guide simple à suivre, notamment pour les débutants. 🙂

La plupart de ces règles ne sont pas tirées de mon chapeau (que je ne porte pas), mais des deux mastodontes [Google](https://google.github.io/styleguide/jsguide.html) et [AirBnB](https://github.com/airbnb/javascript/blob/master/README.md) ainsi que du fameux ouvrage *Clean code* de *Robert C.Martin*.

Cependant, j'admets aussi l'avoir aggrémenté d'une petite touche personnelle. Ne m'en voulez pas trop... 😏

Voici le sommaire :

1. [Commentaires](#commentaires)
2. [Nommage](#nommage-des-variables-fonctions)
3. [Chaînes de caractères](#chaines-de-caractères)
4. [Blocs de code](#instructions-et-blocs-de-code-fonctions-conditions-boucles)
5. [Variables](#déclaration-des-variables)
6. [Conditions](#conditions)
7. [Boucles](#boucles)
8. [Fonctions](#fonctions)
9. [Tableaux](#tableaux)
10. [Objets](#objets)

## Commentaires

- Utiliser la syntaxe courte ou longue suivie d'un espace
- Garder la même syntaxe dans tout le code
- Mettre de la ponctuation (majuscule au début, point à la fin, virgules éventuelles)
- Le commentaire doit toujours se situer juste au dessus du code commenté

```js
// Ceci est un commentaire sur le premier console.log.
console.log("Le commentaire du dessus me concerne !");

/* Ceci est un commentaire sur le deuxième console.log. */
console.log("Le commentaire du dessus me concerne !");
```

En cas de syntaxe multiligne, faire commencer chaque nouvelle ligne par une étoile située juste en dessous de l'étoile précédente suivie d'un espace.

```js
/* Ceci est
 * encore un commentaire
 * sur le console.log.
 */
console.log("Le commentaire du dessus me concerne !");
```

**Le code devrait dans l'idéal se suffir à lui-même. Éviter l'abus de commentaires en écrivant du code explicite.**

## Nommage des variables, fonctions...

- Privilégier l'anglais (sauf si vous voulez jouer au rebelle patriote)
- Casing : **camelCase** (ça c'est non négociable)
- Noms clairs, il faut éviter les abréviations ambiguës et les noms trops longs  
- Les variables booléennes devraient être préfixées par un *is* ou un *has*
- Les fonctions devraient être préfixées par un verbe
- Garder un vocabulaire cohérent dans tout le code

```js
// anglais, nom correct, camelCase
let goodTitle = 'Simple JS Style Guide';
// abréviation facile à comprendre
let msg = `It's ok !`;
// préfix is / has sur les variables booléennes
let isMajor = true;
let hasRights = false;

// ici on utilise le verbe "get" pour la fonction de récupération
function getRules() {
  // récupération des règles
}
// on le réutilise ici aussi pour garder une cohérence
function getBadJokes() {
  // récupération des blagues nulles
}
```

## Chaînes de caractères

Utiliser les apostrophes plutôt que les guillemets.

```js
const aGoodString = 'Une chaine qui a du caractère...'; // pas "Une chaine qui a du caractère..."
```

Cependant, lorsqu'il y a des apostrophes dans la chaîne ou qu'il y a besoin de passer des lignes il faut privilégier l'utilisation des backticks (littéraux de gabarits). 
Cela permet d'éviter d'avoir recours à l'échappement ou la concaténation.

```js
const hardToSay = `Essaie de prononcer ça correctement : 
"Les chaussettes de l'archiduchesse sont-elles sèches ? Archi-sèches !"`;
```

La concaténation est également évitée lorsqu'on veut y inclure des variables ou des appels de fonction.
Pas d'espaces entre les accolades et l'expression.

```js
const superLanguage = 'JavaScript';
const superString = `Ma super chaine en ${langageName} !`; // pas ${ langageName }
```

## Instructions et blocs de code (fonctions, conditions, boucles...)

- Point-virgule à la fin de chaque instruction.
- Une instruction par ligne dans un bloc de code.
- Indentation des instructions dans un bloc : 2 espaces.  
- Privilégier la syntaxe étendue à la syntaxe sur une seule ligne lorsque les {} sont obligatoires.  
- Faire débuter le bloc de code sur la première ligne. Finir le bloc de code sur une nouvelle ligne.  
- Pas d'espace entre le nom d'une fonction / le mot clef if / while / for et la paire de parenthèses.  
- Pas d'espace entre la paire de parenthèses et ce qu'il y a dedans. Espace entre les paramètres.  
- Ligne vide en dessous du bloc de code.  

```js
// Création de fonction
function superFunction(foo, bar) {
  console.log('Une première instruction !');
  console.log('Une deuxième instruction !');
}

// Utilisation de fonction
superFunction('machin', 'truc');
```

Espaces entre les opérateurs et les opérandes.

```js
if(age >= 18 && espece === 'humain') {
  console.log('Il est majeur !');
}
```

## Déclaration des variables

Utiliser les mots clés *let* ou *const*, pas *var*. L'idée est d'éviter la création de variables globales.

```js
// utiliser let si la valeur est amenée à être modifiée
let score = 40;
score += 2;

// utiliser const si la valeur reste fixe
const gameName = 'Super jeu';
```

Lorsqu'on veut déclarer plusieurs variables il faut répéter le mot clef, ligne par ligne.

```js
// une déclaration par ligne, faire de même pour les const
let firstVar = 1;
let secondVar = 2;
let thridVar = 3;
```

Grouper toutes les const puis grouper toutes les let.

```js
// les const d'un côté
const firstConst = 'Ca changera pas';
const secondConst = 'Ca non plus...';
// les let de l'autre
let firstVar = 'Par contre ça oui';
let secondVar = 'et ça aussi...';
```

Ne pas utiliser le chainage d'assignations car cela créé des variables globales.

```js
// ne pas faire let a = b = c = 'truc'; mais plutôt :
let a = 'truc';
let b = a;
let c = a;
```

**Déclarer et initialiser les variables au bon moment, et pas forcément au début d'un bloc de code.**

## Conditions

Dans le cas d'une condition if / else, mettre le else au même niveau que la fin du bloc if.

```js
if(test) {
  // ...
} else {
  // ...
}
```

Si il n'y a qu'une instruction executée dans une condition et qu'il n'y a pas de else, on peut choisir d'omettre les {} et écrire l'instruction sur une seule ligne.

```js
// ne pas mettre l'instruction sur une nouvelle ligne si vous ne mettez pas les {} et qu'il n'y a pas de else
if(test) return true;
```

Dans une fonction, en cas de return dans un if, il est inutile de mettre le else.

```js
// si on entre dans le if on sort de la fonction grâce au return...
if(test) return true;

// ... le code qui suit n'est donc pas lu (sauf si le test est faux bien sûr)
return false;
```

Pour tester une égalité, privilégier l'égalité stricte. De même pour l'inégalité.

```js
// on privilégie === au == et !== au !=
if(email === 'labonneadresseemail@gmail.com') {
  // ...
}
```

Utiliser la syntaxe raccourcie si le test porte sur une valeur booléenne.

```js
// ici on a une variable booléenne, donc...
const isMajor = true;
// ... on privilégie l'utilisation du raccourci au lieu de === true / false
if(isMajor) {
  console.log('Il est majeur !');
}
```

Ne pas utiliser la syntaxe raccourcie si la valeur testée n'est pas une valeur booléenne.

```js
// là par contre on a un nombre et une chaine de caractère...
const zero = 0;
const strVide = '';
// même si on pourrait les tester avec un if(!zero || !strVide) on va plutôt détailler
if(zero === 0 || strVide === '') {
  console.log('C\'est falsy !');
}
```

En cas d'une condition switch formater comme suit :

```js
switch(cart) {
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

Les ternaires doivent être écrites sur une seule ligne et ne doivent pas être imbriquées.

```js
const statut = (age >= 18) ? 'majeur' : 'mineur';
```

Utiliser les syntaxes raccourcies en cas de possibilité.

```js
// on simule une non réception de données
const data = null; 
// on applique 5 à la variable limit au cas où data ne possède rien
const limit = data.limit || 5; // pas const limit = data.limit ? data.limit : 5;
```

## Boucles

Nommer ses variables d'incrément *i*, *j* ou *k* dans les boucles est OK (c'est une convention).

L'itérateur dans une boucle for doit être déclarée avec le mot clef *let*.

```js
for(let i = 0; i < 10; i++) {
  // ...
}
```

Éviter les nombres magiques (nombres qui trainent dans le code sans qu'on sache à quoi ils font référence).

```js
const numberOfPotatoes = 10;

for(let i = 0; i < numberOfPotatoes; i++) { // pas i < 10
  // ...
}
```

## Fonctions

Une fonction doit être déclarée dans un module. Elle peut être exportée ou non. 

**Une fonction doit principalement s'occuper d'une seule tâche.**  
Si une fonction devient trop lourde, alors il faut la diviser en plusieurs autres fonctions.

Pour déclarer une fonction, privilégier la syntaxe fléchée au mot clé function.

```js
// pas function aGoodFunction { ... }
const aGoodFunction = (str) => {
  // ...
}

```

De même pour les fonctions de callback.

```js
const truc = array.find((elem) => elem === 'surprise');
```

Il faut éviter de mettre en dur des valeurs en arguments. Il faut d'abord les insérer dans des variables pour les passer ensuite à la fonction.

```js
const min = 0;
const max = 100;

// pas appelFonction(1, 100);
appelFonction(min, max);
```

Eviter de passer plus de trois arguments à une fonction. Privilégier le passage d'un objet de configuration qui contient tout ce qu'il faut.

```js
const options = {
  min: 0,
  max: 100,
  // ...
}
// pas appelFonction(min, max, ...)
appelFonction(options);
```

## Tableaux

Utiliser la syntaxe littérale pour créer un tableau.

```js
// pas new Array(length)
const array = [
  'elem1',
  'elem2',
  // ...
]
```

Utiliser la méthode *push()* pour insérer un élément dans un tableau.

```js
const array = [
  'elem1',
  'elem2'
];
// pas array[2] = 'elem3'
array.push('elem3');
```

Pour combiner plusieurs tableaux en un seul, utiliser l'opérateur spread.
Pas d'espace après l'opérateur.

```js
const cats = ['chat', 'tigre', 'lion'];
const dogs = ['chien', 'renard', 'loup'];

const animals = [...cats, ...dogs];
```

## Objets

### Objets littéraux

Utiliser la syntaxe littérale pour créer un objet.

```js
// pas new Object()
const obj = { 
  prop: 'valeur',
  prop2: 'valeur',
  // ...
}
```

La déclaration des méthodes doit se faire avec le mot clef *function*.
Il ne faut pas utiliser la syntaxe fléchée.

```js
const obj = {
  // pas aMethod: () => { ... }
  aMethod: function() {
    // ...
  }
}
```

Ne pas mettre de contexte inutile dans le nom des méthodes et des propriétés.

```js
// ici on sait qu'on a une pizza, donc...
const pizza = {
  base: 'creme fraiche', // inutile d'écrire pizzaBase...
  ingredients: ['ananas', 'lardons', 'mozza'] // ni pizzaIngredients...
  // ni pizzaToString
  toString: function() {
    // ...
  }
}
```

### POO

Les noms de classes doivent commencer par une majuscule.  
Espace entre le nom de la classe et le début du bloc de code.

```js
class Pizza {

}
```
