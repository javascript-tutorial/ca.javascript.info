# Comentaris

Com sabem pel capítol <info:structure>, els comentaris poden ser d'una única línia: començant amb `//` o de múltiples línies: `/* ... */`.

Normalment els utilitzem per descriure com i perquè funciona el codi.

<<<<<<< HEAD
A primera vista, comentar pot semblar obvi, però els novells de la programació acostumen a equivocar-se.
=======
At first sight, commenting might be obvious, but novices in programming often use them wrongly.
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

## Comentaris dolents

Els novells acostumen a utilitzar comentaris per explicar "que està passant en el codi". Per exemple:

```js
// Aquest codi farà això (...) i això (...)
// ...i qui sap que més...
very;
complex;
code;
```

<<<<<<< HEAD
Però en bon codi, la quantitat de comentaris "explicatius" hauria de ser mínima. De debò, el codi hauria de ser fàcil d'entendre sense comentaris.
=======
But in good code, the amount of such "explanatory" comments should be minimal. Seriously, the code should be easy to understand without them.
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

Existeix una gran norma sobre això: "si el codi és tan poc clar que necessita un comentari, llavors potser hauria de ser reescrit en comptes".

### Recepta: funcions externes

De vegades és millor substituir un tros de codi amb una funció: així:

```js
function showPrimes(n) {
  nextPrime:
  for (let i = 2; i < n; i++) {

*!*
    // comprova si i és un nombre primer
    for (let j = 2; j < i; j++) {
      if (i % j == 0) continue nextPrime;
    }
*/!*

    alert(i);
  }
}
```

La millor versió, amb una funció externa `isPrime`:

```js
function showPrimes(n) {

  for (let i = 2; i < n; i++) {
    *!*if (!isPrime(i)) continue;*/!*

    alert(i);  
  }
}

function isPrime(n) {
  for (let i = 2; i < n; i++) {
    if (n % i == 0) return false;
  }

  return true;
}
```

Ara podem entendre el codi fàcilment. La funció mateixa es transforma en el comentari. Aquest tipus de codi s'anomena "auto descriptiu".

### Recepta: crea funcions

I si tenim una llarga "llista de codi" com aquesta:

```js
// aquí afegim whisky
for(let i = 0; i < 10; i++) {
  let drop = getWhiskey();
  smell(drop);
  add(drop, glass);
}

// aquí afegim suc
for(let t = 0; t < 3; t++) {
  let tomato = getTomato();
  examine(tomato);
  let juice = press(tomato);
  add(juice, glass);
}

// ...
```

Llavors pot ser una millor variant si reescrivim en funcions com:

```js
addWhiskey(glass);
addJuice(glass);

function addWhiskey(container) {
  for(let i = 0; i < 10; i++) {
    let drop = getWhiskey();
    //...
  }
}

function addJuice(container) {
  for(let t = 0; t < 3; t++) {
    let tomato = getTomato();
    //...
  }
}
```

De nou, les pròpies funcions ens expliquen el que està passant. No hi ha res a comentar. I també l'estructura del codi és millor quan la dividim. Queda clar el que fa cada funció, que rep i que retorna.

En realitat, podem evitar totalment els comentaris "explicatius". Existeixen algoritmes complexos. Hi ha "trucs" intel·ligents amb motius d'optimització. Però generalment hauríem d'intentar mantenir el codi simple i auto explicatiu.

## Bons comentaris

Per tant, els comentaris explicatius solen ser dolents. Quins comentaris són bons?

<<<<<<< HEAD
Descriuen l'arquitectura:
: Proporcionen una visió general d'alt nivell dels components, com interactuen, quin és el flux de control en diferents situacions... En resum -- una vista d'ocell del codi. Hi ha un llenguatge de diagrames especial [UML](https://ca.wikipedia.org/wiki/Llenguatge_de_modelitzaci%C3%B3_unificat) per a diagrames d'arquitectura d'alt nivell. Sens dubte val la pena estudiar.

Documenten l'ús d'una funció:
: Hi ha una sintaxi especial [JSDoc](http://en.wikipedia.org/wiki/JSDoc) per a documentar funcions: l'ús, els paràmetres i els valors retornats. 
=======
Describe the architecture
: Provide a high-level overview of components, how they interact, what's the control flow in various situations... In short -- the bird's eye view of the code. There's a special language [UML](http://wikipedia.org/wiki/Unified_Modeling_Language) to build high-level architecture diagrams explaining the code. Definitely worth studying.

Document function parameters and usage
: There's a special syntax [JSDoc](http://en.wikipedia.org/wiki/JSDoc) to document a function: usage, parameters, returned value.
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

	Per exemple:
	For instance:
    ```js
    /**
     * Retorna x elevat a la potència de n.
     *
     * @param {number} x El número a elevar.
     * @param {number} n La potència, ha de ser un número natural.
     * @return {number} x elevat a la potència de n.
     */
    function pow(x, n) {
      ...
    }
    ```
	
	Aquest tipus de comentaris ens permeten entendre la finalitat de la funció i com utilitzar-la de la manera correcta sense mirar el codi.
	Per cert, molts editors com [WebStorm](https://www.jetbrains.com/webstorm/) també els poden entendre i utilitzar-los per proveir auto complete i algun tipus de comprovació automàtica del codi.
	
	També hi ha eines com [JSDoc 3](https://github.com/jsdoc3/jsdoc) que poden generar documentació en HTML a partir dels comentaris. Pots llegir més informació sobre JSDoc a <http://usejsdoc.org/>.
	
Per què el problema està resolt d'aquesta manera?
: El que està escrit és important. Però el que *no* està escrit pot ser inclòs més important per entendre el que està passant. Per què el problema està resolt d'aquesta manera específica? El codi no ens dóna cap resposta.

	Si hi han diferents maneres de resoldre el problema, per què aquesta? Especialment quan no és la més obvia. 
	
	Sense aquest tipus de comentaris la següent situació pot ocórrer:
	1. Tu (o el teu company) obres el codi escrit ja fa un temps, i veus que és "sub-optim".
	2. Penses: "Que ximple que vaig ser, i que intel·ligent  que sóc ara", i reescrius el codi utilitzant la "manera més obvia i correcta".
	3 ... El desig de reescriure era bo. Però durant el procés et dónes compte que la solució "més obvia" en realitat falla. Inclòs recordes vagament per què, perquè ja ho vas provar fa temps. Retornes a la variant correcta, però has perdut temps.
	
	Els comentaris que ens expliquen la solució són molt importants. Ens ajuden a continuar el desenvolupament de manera correcta.
	
Hi ha algunes característiques subtils del codi? A on són utilitzades?
: Si el codi té alguna cosa subtil i contra intuïtiva, definitivament val la pena comentar-la.

## Resum

Un signe important d'un bon desenvolupador són els comentaris: la seva presència i fins i tot la seva absència.

Bons comentaris ens ajuden a mantenir el codi de manera correcta, tornar després d'un temps i utilitzar-lo de manera eficient.

**Comenta això:**

- Arquitectura en general, punts de vista d'alt nivell.
- Utilització de funcions.
- Solucions importants, especialment quan no són les immediatament obvies.

**Evita comentaris:**

<<<<<<< HEAD
- Que ens expliquen "com funciona el codi" i "que és el que fa".
- Escriu-los només si és impossible fer que el codi sigui simple i auto descriptiu fins al punt que no els necessiti.
=======
- That tell "how code works" and "what it does".
- Put them in only if it's impossible to make the code so simple and self-descriptive that it doesn't require them.
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

Els comentaris també són utilitzats per eines de documentació automàtica com JSDoc3: els llegeixen i generen documents en HTML (o documents en altres formats).
