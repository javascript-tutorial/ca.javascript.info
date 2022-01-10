# El mode modern, "use strict"

Durant molt de temps, JavaScript ha evolucionat sense problemes de compatibilitat. S'han afegit funcions noves al llenguatge mentre que les funcions antigues no han canviat.

Això tenia l'avantatge de no trencar mai el codi existent. Però l'inconvenient era que qualsevol errada o decisió imperfecta dels creadors de JavaScript es quedés en el llenguatge per sempre.

<<<<<<< HEAD
Aquest era el cas fins al 2009, quan va aparèixer ECMAScript 5 (ES5). Afegia noves característiques al llenguatge i modificava algunes de les existents. Per mantenir el codi antic funcionant, la majoria de les modificacions estan desactivades per defecte. Necessites activar-les explícitament amb una directiva especial: `"use strict"`.
=======
This was the case until 2009 when ECMAScript 5 (ES5) appeared. It added new features to the language and modified some of the existing ones. To keep the old code working, most such modifications are off by default. You need to explicitly enable them with a special directive: `"use strict"`.
>>>>>>> 246c600f11b4e6c52b4ae14f83e65319671f998f

## "use strict"

La directiva és com una string: `"use strict"` o `'use strict'`. Quan es troba a la part superior d'un script, tot el script funciona de manera "moderna".

Per exemple:

```js
"use strict";

// aquest codi funciona de manera moderna
...
```

<<<<<<< HEAD
Aprendrem a utilitzar funcions (una manera d'agrupar instruccions) aviat.

D'ara endavant, tingueu en compte que `"use strict"` es pot posar al principi de la majoria de tipus de funcions en comptes de tot el script. Fer això només habilita el mode estricte en aquesta funció. Però habitualment, la gent ho utilitza per a tot el script.

=======
Quite soon we're going to learn functions (a way to group commands), so let's note in advance that `"use strict"` can be put at the beginning of a function. Doing that enables strict mode in that function only. But usually people use it for the whole script.
>>>>>>> 246c600f11b4e6c52b4ae14f83e65319671f998f

````warn header="Assegureu-vos que \"use strict\" està a la part superior"
Si us plau, assegureu-vos que `"use strict"` és a la part superior dels vostres scripts, o per al contrari, pot ser que el mode estricte no estigui habilitat.

El mode estricte no està habilitat aquí:

```js no-strict
alert("some code");
// l'"use strict" de sota s'ignora--ha d'estar a la part superior

"use strict";

// el mode estricte no està activat
```

Només comentaris poden aparèixer per sobre d'`"use strict"`.
````

```warn header="No hi ha cap manera per a cancel·lar el `use strict`"
No existeix cap directiva semblant a `"no use strict"` que retorna el motor al comportament antic.

<<<<<<< HEAD
Quan entrem al mode estricte, no hi ha retorn.
=======
Once we enter strict mode, there's no going back.
>>>>>>> 246c600f11b4e6c52b4ae14f83e65319671f998f
```

## Consola del navegador

<<<<<<< HEAD
Per al futur, quan utilitzeu la consola del navegador per provar funcions, tingueu en compte que no fa servir l'`use strict` per defecte.
=======
When you use a [developer console](info:devtools) to run code, please note that it doesn't `use strict` by default.
>>>>>>> 246c600f11b4e6c52b4ae14f83e65319671f998f

De vegades, quan `use strict` fa una diferència, obtindreu resultats incorrectes.

<<<<<<< HEAD
Podem teclejar `key:Shift+Enter` per introduir línies múltiples, i posar `use strict` a la part superior, així:

```js
'use strict'; <Shift+Enter for a newline>
//  ...el teu codi
<Enter to run>
```

Funciona en la majoria de navegadors, com Firefox i Chrome.

Si no és així, la manera més segura de garantir el mode estricte seria introduint el codi a la consola d'aquesta manera:
=======
So, how to actually `use strict` in the console?

First, you can try to press `key:Shift+Enter` to input multiple lines, and put `use strict` on top, like this:

```js
'use strict'; <Shift+Enter for a newline>
//  ...your code
<Enter to run>
```

It works in most browsers, namely Firefox and Chrome.

If it doesn't, e.g. in an old browser, there's an ugly, but reliable way to ensure `use strict`. Put it inside this kind of wrapper:
>>>>>>> 246c600f11b4e6c52b4ae14f83e65319671f998f

```js
(function() {
  'use strict';

<<<<<<< HEAD
  // ...el teu codi...
})()
```

## Sempre "use strict"

Encara hem d'explicar les diferències entre el mode estricte i el mode "per defecte".

En els capítols següents, a mesura que aprenguem com funciona el llenguatge, explicarem les diferències entre el mode estricte i el per defecte. Per sort, no hi ha gaires diferències i en realitat ens fan la vida més senzilla.

Per ara, n'hi ha prou de saber-ho en general:

1. La directiva `"use strict"` canvia el motor al mode "modern", canviant el comportament d'algunes funcions integrades. Veurem els detalls més endavant en el tutorial.
2. El mode estricte s'habilita col·locant `"use strict"` a la part superior d'un script o funció. Diferents funcions del llenguatge, com ara les "classes" i "modules", activen el mode estricte automàticament.
3. Tots els navegadors moderns suporten el mode estricte.
4. Es recomana sempre començar els scripts amb `"use strict"`.  Tots els exemples d'aquest tutorial fan servir el mode estricte excepte que (molt  poques vegades) s'especifiqui el contrari.
=======
  // ...your code here...
})()
```

## Should we "use strict"?

The question may sound obvious, but it's not so.

One could recommend to start scripts with `"use strict"`... But you know what's cool?

Modern JavaScript supports "classes" and "modules" - advanced language structures (we'll surely get to them), that enable `use strict` automatically. So we don't need to add the `"use strict"` directive, if we use them.

**So, for now `"use strict";` is a welcome guest at the top of your scripts. Later, when your code is all in classes and modules, you may omit it.**

As of now, we've got to know about `use strict` in general.

In the next chapters, as we learn language features, we'll see the differences between the strict and old modes. Luckily, there aren't many and they actually make our lives better.

All examples in this tutorial assume strict mode unless (very rarely) specified otherwise.
>>>>>>> 246c600f11b4e6c52b4ae14f83e65319671f998f
