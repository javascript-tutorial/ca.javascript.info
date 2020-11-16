# Estructura del codi

Els blocs que formen el codi són el primer que estudiarem.

## Sentències

Les sentències són construccions sintàctiques i comandes que duen a terme accions.

Ja hem vist una sentència, `alert('Hola, món!')`, que mostra el missatge "Hola, món!".

Al nostre codi podem tenir tantes sentències com vulguem. Les sentències es poden separar amb un punt i coma.

Per exemple, aquí separem "Hola món" en dues alertes:

```js run no-beautify
alert('Hola'); alert('món');
```

Normalment, les sentències s'escriuen en línies separades per fer el codi més llegible.

```js run no-beautify
alert('Hola');
alert('món');
```

## Punts i coma [#semicolon]

Generalment, el punt i coma es pot ometre quan hi ha un salt de línia.

Això també funcionaria:

```js run no-beautify
alert('Hola')
alert('món')
```

Aquí, JavaScript interpreta el salt de línia com a un punt i coma "implícit". Això s'anomena [inserció de punt i coma automàtica](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion).

**En la majoria dels casos, una nova línia implica un punt i coma. Però "en la majoria dels casos" no és "sempre"!**

Hi ha casos en què una nova línia no implica un punt i coma. Per exemple:

```js run no-beautify
alert(3 +
1
+ 2);
```

El codi retorna `6` perquè JavaScript no insereix punts i coma aquí. És intuïtivament obvi que si la línia acaba amb un signe més `"+"`, llavors és una "expressió incompleta", així que el punt i coma no fa falta. I en aquest cas funciona com s'espera.

**Però hi ha situacions on JavaScript "falla" a l'assumir un punt i coma on realment fa falta.**

Aquests tipus d'error són força difícils de trobar i solucionar.

````smart header="Exemple d'error"
Si teniu curiositat per veure un exemple concret d'aquests errors, vegeu aquest codi:

```js run
[1, 2].forEach(alert)
```

Ara mateix no importa què signifiquen els claudàtors `[]` i `forEach`. Els estudiarem més endavant. Per ara, només cal que recordeu el resultat del codi: mostra `1` i després `2`.

Ara, afegim un `alert` abans del codi i *no* li posem un punt i coma final:

```js run no-beautify
alert("Hi haurà un error")

[1, 2].forEach(alert)
```

Ara, si executem el codi, només el primer `alert` es mostra i llavors hi ha un error!

Però tot torna a funcionar si afegim un punt i coma després de l'`alert`:
```js run
alert("Tot va bé");

[1, 2].forEach(alert)  
```

Ara tenim el missatge de "Tot va bé" seguit d'un `1` i un `2`.


L'error a la versió sense punt i coma passa perquè JavaScript no assumeix cap punt i coma abans d'uns claudàtors `[...]`.

Llavors, com el punt i coma no s'insereix automàticament, el codi del primer exemple és tractat com una sola sentència. El motor ho veu així:

```js run no-beautify
alert("Hi haurà un error")[1, 2].forEach(alert)
```

Però haurien de ser dues sentències separades, no una. Aquesta fusió, en aquest cas, és incorrecta, i d'aquí surt l'error. Això pot passar en altres situacions.
````

Recomanem posar punts i coma entre sentències encara que estiguin separades per salts de línia. Aquesta norma té una gran adopció per part de la comunitat. Ho comentem un altre cop -- *és possible* obviar els punts i coma la majoria dels cops. Però és més segur -- sobretot per a principiants -- emprar-los.

<<<<<<< HEAD
## Comentaris
=======
## Comments [#code-comments]
>>>>>>> 99e59ba611ab11319ef9d0d66734b0bea2c3f058

Conforme passa el temps, els programes esdevenen més i més complexos. Esdevé necessari afegir *comentaris* que descriuen què fa el codi i per què ho fa.

Els comentaris es poden posar a qualsevol lloc d'un script. No afecten llur execució perquè el motor simplement els ignora.

**Els comentaris d'una línia comencen amb dos barres `//`.**

La resta de la línia és un comentari. Pot ocupar una línia sencera o bé seguir una sentència.

Com aquí:
```js run
// Aquest comentari ocupa una línia sencera ell sol
alert('Hola');

alert('món'); // Aquest comentari segueix la sentència
```

**Els comentaris multilínia van precedits d'una barra i un asterisc <code>/&#42;</code> i acaben amb un asteris i una barra <code>&#42;/</code>.**

Com aquí:

```js run
/* Un exemple amb dues línies.
Això és un comentari multilínia.
*/
alert('Hola');
alert('món');
```

El contingut dels comentaris s'ignora, així que si hi posem codi a dins <code>/&#42; ... &#42;/</code>, no s'executarà.

A vegades és útil per desactivar temporalment una part del codi:

```js run
/* Comentant el codi
alert('Hola');
*/
alert('món');
```

<<<<<<< HEAD
```smart header="Empreu dreceres de teclat!"
En la majoria dels editors, una línia de codi es pot comentar prement la drecera de teclat `key:Ctrl+/` per a un comentari d'una línia i alguna cosa similar a `key:Ctrl+Shift+/` -- per comentaris multilínia (seleccioneu un fragment de codi i premeu la drecera). Per Mac, proveu `key:Cmd` en lloc de `key:Ctrl`.
=======
```smart header="Use hotkeys!"
In most editors, a line of code can be commented out by pressing the `key:Ctrl+/` hotkey for a single-line comment and something like `key:Ctrl+Shift+/` -- for multiline comments (select a piece of code and press the hotkey). For Mac, try `key:Cmd` instead of `key:Ctrl` and `key:Option` instead of `key:Shift`.
>>>>>>> 99e59ba611ab11319ef9d0d66734b0bea2c3f058
```

````warn header="No es suporten comentaris aniuats!"
No hi ha d'haver `/*...*/` dins d'un altre `/*...*/`.

Aquest codi patirà un error:

```js run no-beautify
/*
  /* comentari aniuat ?!? */
*/
alert( 'Món' );
```
````

Per favor, no dubteu en comentar el vostre codi.

Els comentaris incrementen l'impacte total del codi, però això no suposa cap problema. Hi ha diverses eines que minimitzen el codi abans de publicar-lo a un servidor de producció. Eliminen els comentaris perquè no apareguin als scripts finals. Per tant, els comentaris no tenen cap efecte negatiu a producció.

Més endavant trobareu un capítol anomenat <info:code-quality> que també explica com escriure millors comentaris.
