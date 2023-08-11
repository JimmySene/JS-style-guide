# Simple JS Style Guide

**Comment écrire proprement du code JavaScript ?**

Voilà qui pourrait faire naître un débat aussi intense qu'el famoso **Pain au chocolat VS Chocolatine** ! 😲

J'exagère ? Sans doute un peu.

Mais force est de reconnaître que certaines règles de style JS semblent plébiscitées par tous, quand d'autres au contraire semblent parfois se contredire... 🙄

L'idée de ce guide est de vous inciter à appliquer un style de code JavaScript efficace, simple et rapide à mettre en place. Je l'ai conçu en ayant à l'esprit de toujours garder l'essentiel, tout en enlevant le superflu pour éviter qu'il ne devienne trop complexe. Ainsi, même les débutants pourront le comprendre et le mettre en pratique. 🙂

La plupart de ces recommandations ne sont pas tirées de mon chapeau (que je ne porte pas), mais des deux mastodontes [Google](https://google.github.io/styleguide/jsguide.html) et [AirBnB](https://github.com/airbnb/javascript/blob/master/README.md) ainsi que du fameux ouvrage *Clean code* de *Robert C.Martin*. Cependant, j'y ai aussi apporté ma petite touche personnelle, ne serait-ce que pour trancher le débat quand il le fallait. 😉

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

Les commentaires doivent :

- être limités au profit d'un code auto-suffisant ;
- être utiles, clairs et concis ;
- être ponctués ou non (garder la même logique dans tout le code) ;
- être placés soit au dessus, soit à droite du code à commenter suivi d'un espace.

Ils peuvent être écrits en syntaxe courte `//` (à privilégier quand c'est possible) ou longue `/* */` :

- en cas de syntaxe courte, mettre un espace après le `//` ;
- en cas de syntaxe longue, mettre un espace après le `/*` et avant le `*/`.

```js
// Ceci est une bonne syntaxe de commentaire.
console.log("Syntaxe courte."); // ceci aussi

/* Ceci également ! Même si dans ce contexte, on privilégiera la syntaxe courte. */
console.log("Syntaxe multiligne."); /* pareil ici */
uneFonction(unParam /* en revanche là, on ne peut pas faire autrement */, unDeuxiemeParam);
```

En cas de commentaire multiligne, privilégier la syntaxe longue en faisant commencer chaque nouvelle ligne par une *, située juste en dessous de la précédente, suivie d'un espace :

```js
/* 
 * Ceci est encore
 * une bonne syntaxe
 * de commentaire.
 */
console.log("Commentaire multiligne.");

// cependant
// cette syntaxe est également possible
// même si on priviligiera celle du dessus
console.log("Un autre commentaire multiligne.");
```

Utiliser les commentaires [JSDoc](https://jsdoc.app/) pour les déclarations de fonction, ainsi que des attributs et méthodes de classe.

## Nommage des variables, fonctions...

Le nommage des différents éléments du code doit :

- utiliser une même langue, idéalement l'anglais (sauf si vous voulez jouer au rebelle patriote) ;
- utiliser le camelCase (variables, propriétés, méthodes) et PascalCase (classes) ;
- être clair et concis, il faut éviter les abréviations ambiguës et les noms trops longs ;  
- être préfixés par un *is* ou un *has* si variables ou fonctions booléennes ;
- être préfixés par un verbe d'action si fonctions (get, add, remove, set...).

```js
// anglais, nom correct, camelCase
let goodTitle = "Simple JS Style Guide";
// abréviation facile à comprendre
let okMsg = "It's ok !";
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

Lorsqu'on écrit une chaine de caractère, on doit :

- utiliser les apostrophes ('') ou les guillemets (""), puis s'y tenir dans tout le code ; 
- éviter les échappements et les concaténations en utilisant les backticks (``) ;
- lors de l'utilisation des backticks, ne pas mettre d'espaces avant ni après les accolades.

```js
// guillemets (ma préférence personnelle car il y a beaucoup d'apostrophes dans les phrases en français)
const aGoodString = "Une chaine qui a du caractère...";
// apostrophes (on les privilégie souvent quand on inclus des balises HTML avec attributs qui nécessitent l'usage des guillemets)
const anotherGoodString = 'Elle est pas mal celle là !';
// backticks (permet d'éviter l'échappement des apostrophes / guillemets et la concaténation due au multiligne ou à l'interpolation de variables / fonctions)
const laughEmoji = "🤣";
const hardToSay = `Essaie de prononcer ça correctement : 
"Les chaussettes de l'archiduchesse sont-elles sèches ? Archi-sèches !" ${laughEmoji}`; // et pas ${ laughEmoji }
```

## Instructions et blocs de code (fonctions, conditions, boucles...)

Voici quelques règles générales concernant les blocs de code `{}` :

- faire débuter le bloc de code sur la ligne du mot clé utilisé ;
- écrire son contenu sur une ou plusieurs nouvelles lignes ;
- finir le bloc de code sur une nouvelle ligne ;  
- mettre un espace après chaque mot clé ;  
- mettre un espace entre `)` et `{` ;
- ne pas mettre d'espace entre les parenthèses et leur contenu `(...)` ;  
- mettre une ligne vide en dessous du bloc de code.

Ainsi que leur contenu :

- point-virgule à la fin de chaque instruction ;
- pas d'espace entre l'instruction et le point-virgule ;
- une seule instruction par ligne ;
- indentation de 2 espaces avant chaque instruction située dans un bloc.

```js
// Exemple d'un bloc avec création d'une fonction
function superFunction(foo, bar) {
  // les instructions sont sur de nouvelles lignes
  console.log('Une première instruction !'); // indentation de 2 espaces au début
  console.log('Une deuxième instruction !'); // et ; de fin
}

superFunction('machin', 'truc'); // Suite du code en dessous une ligne vide qui le sépare du précédent bloc

// Exemple d'un bloc de condition
if (age >= 18) {
  console.log('Il est majeur !');
}

// On aurait pu l'écrire sur une ligne car elle ne possède qu'une courte instruction
if (age >= 18) console.log('Il est majeur !');
```

## Déclaration des variables

Mettre un espace avant et après :

- les opérateurs d'affectation `= += -= *= /= %= **=` ;
- les opérateurs arithmétiques si il y en a `+ - * / % **`.

**Déclarer et initialiser les variables au bon moment, et pas forcément au début d'un bloc de code.**

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

Ne pas utiliser le chaînage d'assignations car cela créé des variables globales.

```js
// ne pas faire let a = b = c = 'truc'; mais plutôt :
let a = 'truc';
let b = a;
let c = a;
```

## Conditions

Mettre un espace avant et après les opérateurs logiques `&& ||` et de comparaison `> < >= <= == != === !==`.

```js
if (machin > truc && untel <= autre)
```

Dans le cas d'une condition if / else, mettre le else au même niveau que la fin du bloc if.

```js
if (test != null) {
  // ...
} else {
  // ...
}
```

Si il n'y a qu'une courte instruction executée dans une condition et qu'il n'y a pas de else, on peut choisir d'omettre les `{}` et écrire l'instruction sur une seule ligne.

```js
// exemple d'une condition sur une seule ligne
if (test != null) return true;
```

Dans une fonction, en cas de return dans un if, il est inutile de mettre le else.

```js
const test = "Test validé !";
// si on entre dans le if on sort de la fonction grâce au return...
if (test != null) return true;

// ... le code qui suit n'est donc pas lu (sauf si le test est faux bien sûr)
return false;
```

Utiliser la syntaxe raccourcie `if (variable)` si le test porte uniquement sur une valeur booléenne.

```js
// ici on a une variable booléenne, donc...
const isMajor = true;
// ... on privilégie l'utilisation du raccourci au lieu de === true / false
if (isMajor) {
  console.log("Il est majeur !");
}
```

Ne pas utiliser la syntaxe raccourcie si la valeur testée n'est pas une valeur booléenne.

```js
// là par contre on a un nombre et une chaine de caractère...
const zero = 0;
const strVide = '';
// même si on pourrait les tester avec un if(!zero || !strVide) on va plutôt détailler
if (zero === 0 || strVide === '') {
  console.log("C'est falsy !");
}
```

Pour tester une égalité ou une inégalité il faut utiliser les opérateurs stricts `===` et `!==`.  
`==` et `!=` ne sont à utiliser qu'en combinaison avec `null` pour tester si une valeur vaut null ou undefined.

```js
// on privilégie === au == et !== au !=
if (email === "labonneadresseemail@gmail.com") {
  // ...
}

// on vérifie si email vaut null ou undefined
if (email == null) { // et pas if(!email), voir la règle ci-dessus
  // ...
}
```

En cas d'une condition switch, formater comme suit :

```js
switch (cart) {
  case "Bananes":
    console.log("...");
    break;
  case "Citrons":
    console.log("...");
    break;
  default:
    console.log("...");
}
```

Les ternaires doivent être écrites sur une seule ligne et ne doivent pas être imbriquées.

```js
const statut = (age >= 18) ? 'majeur' : 'mineur';
```

Utiliser les syntaxes raccourcies en cas de possibilité.

```js
// on simule une réception de données manquée
const data = null; 
// on applique 5 à la variable limit au cas où data ne possède rien
const limit = data.limit || 5; // pas const limit = data.limit ? data.limit : 5;
```

## Boucles

Nommer ses variables d'incrément *i*, *j* ou *k* dans les boucles est OK (c'est une convention).

L'itérateur dans une boucle for doit être déclarée avec le mot clef *let*.

```js
for (let i = 0; i < 10; i++) {
  // ...
}
```

Éviter les nombres magiques (nombres qui trainent dans le code sans qu'on sache à quoi ils font référence).

```js
const numberOfPotatoes = 10;

for (let i = 0; i < numberOfPotatoes; i++) { // pas i < 10
  // ...
}
```

Privilégier l'utilisation de la boucle *for of* quand il est possible de l'utiliser, notamment lorsqu'il s'agit de parcourir un tableau.

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


Utiliser la syntaxe littérale pour créer un tableau sur une ou plusieurs lignes.

```js
// pas new Array(length)

// tableau sur plusieurs lignes
const array = [
  'elem1',
  'elem2', // , sur le dernier élément
  // ...,
];

// tableau sur une seule ligne
const anotherArray = ['elem1', 'elem2', 'elem3'];
```

Utiliser la méthode *push()* pour insérer un élément dans un tableau.

```js
const array = [
  'elem1',
  'elem2',
];
// pas array[2] = 'elem3'
array.push('elem3');
```

Pour combiner plusieurs tableaux en un seul, utiliser l'opérateur spread `...`.  
Pas d'espace avant ni après l'opérateur.

```js
const cats = ['chat', 'tigre', 'lion'];
const dogs = ['chien', 'renard', 'loup'];

const animals = [...cats, ...dogs];
```

## Objets

### Objets littéraux

Utiliser la syntaxe littérale pour créer un objet sur une ou plusieurs lignes.

```js
// pas new Object()

// objet littéral sur plusieurs lignes
const obj = { 
  prop: 'valeur',
  prop2: 'valeur', // , sur le dernier élément
  // ...
}

// objet littéral sur une ligne
const anotherObj = {prop: 'valeur', prop2: 'valeur'}
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
