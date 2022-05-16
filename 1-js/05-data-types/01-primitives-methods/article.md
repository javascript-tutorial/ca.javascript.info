# Mètodes dels primitius 

<<<<<<< HEAD
Javascript ens permet treballar amb primitius (cadena de caràcters, nombres, etc.) com si fóssen objectes.

També aporta mètodes propiament anomenats. Els estudiarem aviat, però primer veure'm com funciona perquè, per descomptat, els primitius no són objectes (i ho deixarem encara més clar).
=======
JavaScript allows us to work with primitives (strings, numbers, etc.) as if they were objects. They also provide methods to call as such. We will study those soon, but first we'll see how it works because, of course, primitives are not objects (and here we will make it even clearer).
>>>>>>> 2901e0c64590a67d8a2bde1ea76a514d96f80469

Fixem-nos en les distincions claus entre primitius i objectes.

Un primitiu

<<<<<<< HEAD
- Es un valor d'un tipus primitiu.
- Hi ha 6 tipus primitius: `string`, `number`, `boolean`, `symbol`, `null` i `undefined`.
=======
- Is a value of a primitive type.
- There are 7 primitive types: `string`, `number`, `bigint`, `boolean`, `symbol`, `null` and `undefined`.
>>>>>>> 2901e0c64590a67d8a2bde1ea76a514d96f80469

Un objecte

- Es capaç d'emmagatzemar múltiples tipus com a propietats.
- Es poden crear amb `{}`, com ara: `{name: "John", age: 30}`. Hi ha altres tipus d'objectes en Javascript: les funcions, per exemple, són objectes. 

Una de les millors coses dels objectes és que podem emmagatzemar una funció com a propietats.  

```js run
let john = {
  name: "John",
  sayHi: function() {
    alert("Hi buddy!");
  }
};

john.sayHi(); // Hi buddy!
```

Ací hem creat un objecte `john`amb el mètode `sayHi`.

Hi ha objectes integrats de sèrie, com els que que treballen amb dates, errors, elements HTML, etc. Tenen diferents propietats i mètodes. 

Però, aquestes funcionalitats tenen un cost!

<<<<<<< HEAD
Els objectes són més "pesats" que els primitius. Requereixen recursos addicionals per a suportar aquesta maquinària interna. Però com que les propietats i els mètodes són molt útils en programació, el motor de Javascript tracta d'optimitzar-los per a reduir-ne la càrrega. 
=======
Objects are "heavier" than primitives. They require additional resources to support the internal machinery.
>>>>>>> 2901e0c64590a67d8a2bde1ea76a514d96f80469



<<<<<<< HEAD
## Primitius com a objectes
=======
- There are many things one would want to do with a primitive, like a string or a number. It would be great to access them using methods.
- Primitives must be as fast and lightweight as possible.
>>>>>>> 2901e0c64590a67d8a2bde1ea76a514d96f80469

Heus ací la paradoxa a la qual va fer front el creador de Javascript:

- Hi ha moltes coses que hom voldria fer amb una primitiu (com una cadena de caràcters o un nombre). Seria genial accedir-hi a través de mètodes. 
- Els primitius han de ser tan ràpids i lleugers com siga possible.

<<<<<<< HEAD
La solució sembla una mica estranya, però: 

- Els primitius són encara primitius. Un valor únic, com voliem. 
- El llenguatge permet accedir mètodes i propietats de cadenes de caràcters, nombres, booleans i símbols. 
- Per a que això funcione, es crea un "objecte embolcall" que aporta funcionalitats extra, i després es destrueix. 
=======
The "object wrappers" are different for each primitive type and are called: `String`, `Number`, `Boolean`, `Symbol` and `BigInt`. Thus, they provide different sets of methods.

For instance, there exists a string method [str.toUpperCase()](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase) that returns a capitalized `str`.
>>>>>>> 2901e0c64590a67d8a2bde1ea76a514d96f80469

Els "objectes embolcall" són diferents per a cada tipus primitiu i s'anomenen: `String`, `Number`, `Boolean` i `Symbol`. Així, aporten diferents mètodes. 

Per exemple, existeix un mètode [str.toUpperCase()](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase) que retorna una cadena de caràcters en majúscula. 

Heus ací com funciona:

```js run
let str = "Hello";

alert( str.toUpperCase() ); // HELLO
```

Simple, veritat? El que realment ocorre en `str.toUpperCase()`és:

1. La cadena de caràcters `str`és un primitiu. En el moment d'accedir la propietat, un objecte especial es crea, el qual coneix el valor de la cadena i conté mètodes útils, com `toUpperCase()`.
2. El mètode retorna una cadena de caràcters nova (que es mostra amb `alert`).
3. L'objecte especial es destrueix, deixant només el primitiu `str`.

Per tant, els primitius poden tenir mètodes, però mantenir-se lleugers al mateix temps. 

El motor de Javascript optimitza en gran mesura el procés. Fins i tot pot saltar-se la creació de l'objecte addicional. Però s'adhereix al es especificacions i es comporta com si en crees un. 

Un nombre té mètodes propis, per exemple,  [toFixed(n)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed) arrodoneix el número amb la precisió indicada:

```js run
let n = 1.23456;

alert( n.toFixed(2) ); // 1.23
```

Veurem mètodes més específics als capítols <info:number> and <info:string>.

<<<<<<< HEAD
````warn header="Els constructors String/Number/Boolean`són només per a ús intern"
Algunes llenguatges com Java ens permeten crear "objectes embolcall" per a primitius explicitament amb sintaxi de l'estil`new Number(1)` o `new Boolean(false)`.
=======
````warn header="Constructors `String/Number/Boolean` are for internal use only"
Some languages like Java allow us to explicitly create "wrapper objects" for primitives using a syntax like `new Number(1)` or `new Boolean(false)`.
>>>>>>> 2901e0c64590a67d8a2bde1ea76a514d96f80469

En Javascript, això també és possible per raons històriques, però **no és recomanable**. Les coses poden tornar-se imprevisibles.

Per exemple:

```js run
alert( typeof 0 ); // "number"

alert( typeof new Number(0) ); // "object"!
```

Els objectes són sempre s'avaluen com a vertaders en `if`, de manera que l'alerta serà:

```js run
let zero = new Number(0);

if (zero) { // zero is true, because it's an object
  alert( "zero is truthy!?!" );
}
```

Alternativament, emprar les mateixes funcions `String/Number/Boolean` sense `new` és totalment útil i assenyat. Converteixen el valor primitiu corresponent: cadena de caràcters, nombre o booleà.

Per exemple, això és perfectament vàlid: 

```js
let num = Number("123"); // converteix 'string' a 'number'
```
````

​````warn header="null/undefined no tenen mètodes"
Els primitius especials `null` i `undefined` són excepcions. No tenen "objectes embolcall" corresponents i tampoc mètodes. D'alguna forma, són els tipus "més primitius",

L'intent d'accedir a una propietat d'aquest tipus resultaria en error:

​```js run
alert(null.test); // error
````

## Resum

- Els primitius, a excepció de `null`i `undefined`tenen mètodes molt útils. Els estudiarem en els capítols següents. 
- En un sentit estricte, aquests mètodes funcionen a través d'objectes temporals, però els motors de Javascript estan ben preparats per a optimizar-los, de manera que no perjudiquen el rendiment. 