# El mode modern, "use strict"

Durant molt de temps, JavaScript ha evolucionat sense problemes de compatibilitat. S'han afegit funcions noves al llenguatge mentre que les funcions antigues no han canviat.

Aix� tenia l'avantatge de no trencar mai el codi existent. Per� l'inconvenient era que qualsevol errada o decisi� imperfecta dels creadors de JavaScript es qued�s en el llenguatge per sempre.

Aquest era el cas fins al 2009, quan va apar�ixer ECMAScript 5 (ES5). Afegia noves caracter�stiques al llenguatge i modificava algunes de les existents. Per mantenir el codi antic funcionant, la majoria de les modificacions estan desactivades per defecte. Necessites activar-les expl�citament amb una directiva especial: `"use strict"`.

## "use strict"

La directiva �s com una string: `"use strict"` o `'use strict'`. Quan es troba a la part superior d'un script, tot el script funciona de manera "moderna".

Per exemple:

```js
"use strict";

// aquest codi funciona de manera moderna
...
```

Aprendrem a utilitzar funcions (una manera d'agrupar instruccions) aviat.

D'ara endavant, tingueu en compte que `"use strict"` es pot posar al principi de la majoria de tipus de funcions en comptes de tot el script. Fer aix� nom�s habilita el mode estricte en aquesta funci�. Per� habitualment, la gent ho utilitza per a tot el script.


````warn header="Assegureu-vos que \"use strict\" est� a la part superior"
Si us plau, assegureu-vos que `"use strict"` �s a la part superior dels vostres scripts, o per al contrari, pot ser que el mode estricte no estigui habilitat.

El mode estricte no est� habilitat aqu�:

```js no-strict
alert("some code");
// l'"use strict" de sota s'ignora--ha d'estar a la part superior

"use strict";

// el mode estricte no est� activat
```

Nom�s comentaris poden apar�ixer per sobre d'`"use strict"`.
````

```warn header="No hi ha cap manera per a cancel�lar el `use strict`"
No existeix cap directiva semblant a `"no use strict"` que retorna el motor al comportament antic.

Quan entrem al mode estricte, no hi ha retorn.
```

## Consola del navegador

Per al futur, quan utilitzeu la consola del navegador per provar funcions, tingueu en compte que no fa servir l'`use strict` per defecte.

De vegades, quan `use strict` fa una difer�ncia, obtindreu resultats incorrectes.

Podem teclejar `key:Shift+Enter` per introduir l�nies m�ltiples, i posar `use strict` a la part superior, aix�:

```js
'use strict'; <Shift+Enter for a newline>
//  ...el teu codi
<Enter to run>
```

Funciona en la majoria de navegadors, com Firefox i Chrome.

Si no �s aix�, la manera m�s segura de garantir el mode estricte seria introduint el codi a la consola d'aquesta manera:

```js
(function() {
  'use strict';

  // ...el teu codi...
})()
```

## Sempre "use strict"

Encara hem d'explicar les difer�ncies entre el mode estricte i el mode "per defecte".

En els cap�tols seg�ents, a mesura que aprenguem com funciona el llenguatge, explicarem les difer�ncies entre el mode estricte i el per defecte. Per sort, no hi ha gaires difer�ncies i en realitat ens fan la vida m�s senzilla.

Per ara, n'hi ha prou de saber-ho en general:

1. La directiva `"use strict"` canvia el motor al mode "modern", canviant el comportament d'algunes funcions integrades. Veurem els detalls m�s endavant en el tutorial.
2. El mode estricte s'habilita col�locant `"use strict"` a la part superior d'un script o funci�. Diferents funcions del llenguatge, com ara les "classes" i "modules", activen el mode estricte autom�ticament.
3. Tots els navegadors moderns suporten el mode estricte.
4. Es recomana sempre comen�ar els scripts amb `"use strict"`.  Tots els exemples d'aquest tutorial fan servir el mode estricte excepte que (molt  poques vegades) s'especifiqui el contrari.
