# Comentaris

Com sabem pel cap�tol <info:structure>, els comentaris poden ser d'una �nica l�nia: comen�ant amb `//` o de m�ltiples l�nies: `/* ... */`.

Normalment els utilitzem per descriure com i perqu� funciona el codi.

<<<<<<< HEAD
A primera vista, comentar pot semblar obvi, per� els novells de la programaci� acostumen a equivocar-se.
=======
At first sight, commenting might be obvious, but novices in programming often use them wrongly.
>>>>>>> 3699f73b4ccb2a57ac5ef990d2687bf31ccf564c

## Comentaris dolents

Els novells acostumen a utilitzar comentaris per explicar "que est� passant en el codi". Per exemple:

```js
// Aquest codi far� aix� (...) i aix� (...)
// ...i qui sap que m�s...
very;
complex;
code;
```

<<<<<<< HEAD
Per� en bon codi, la quantitat de comentaris "explicatius" hauria de ser m�nima. De deb�, el codi hauria de ser f�cil d'entendre sense comentaris.
=======
But in good code, the amount of such "explanatory" comments should be minimal. Seriously, the code should be easy to understand without them.
>>>>>>> 3699f73b4ccb2a57ac5ef990d2687bf31ccf564c

Existeix una gran norma sobre aix�: "si el codi �s tan poc clar que necessita un comentari, llavors potser hauria de ser reescrit en comptes".

### Recepta: funcions externes

De vegades �s millor substituir un tros de codi amb una funci�: aix�:

```js
function showPrimes(n) {
  nextPrime:
  for (let i = 2; i < n; i++) {

*!*
    // comprova si i �s un nombre primer
    for (let j = 2; j < i; j++) {
      if (i % j == 0) continue nextPrime;
    }
*/!*

    alert(i);
  }
}
```

La millor versi�, amb una funci� externa `isPrime`:

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

Ara podem entendre el codi f�cilment. La funci� mateixa es transforma en el comentari. Aquest tipus de codi s'anomena "auto descriptiu".

### Recepta: crea funcions

I si tenim una llarga "llista de codi" com aquesta:

```js
// aqu� afegim whisky
for(let i = 0; i < 10; i++) {
  let drop = getWhiskey();
  smell(drop);
  add(drop, glass);
}

// aqu� afegim suc
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

De nou, les pr�pies funcions ens expliquen el que est� passant. No hi ha res a comentar. I tamb� l'estructura del codi �s millor quan la dividim. Queda clar el que fa cada funci�, que rep i que retorna.

En realitat, podem evitar totalment els comentaris "explicatius". Existeixen algoritmes complexos. Hi ha "trucs" intel�ligents amb motius d'optimitzaci�. Per� generalment haur�em d'intentar mantenir el codi simple i auto explicatiu.

## Bons comentaris

Per tant, els comentaris explicatius solen ser dolents. Quins comentaris s�n bons?

<<<<<<< HEAD
Descriuen l'arquitectura:
: Proporcionen una visi� general d'alt nivell dels components, com interactuen, quin �s el flux de control en diferents situacions... En resum -- una vista d'ocell del codi. Hi ha un llenguatge de diagrames especial [UML](https://ca.wikipedia.org/wiki/Llenguatge_de_modelitzaci%C3%B3_unificat) per a diagrames d'arquitectura d'alt nivell. Sens dubte val la pena estudiar.

Documenten l'�s d'una funci�:
: Hi ha una sintaxi especial [JSDoc](http://en.wikipedia.org/wiki/JSDoc) per a documentar funcions: l'�s, els par�metres i els valors retornats. 

	Per exemple:
	For instance:
    ```js
    /**
     * Retorna x elevat a la pot�ncia de n.
     *
     * @param {number} x El n�mero a elevar.
     * @param {number} n La pot�ncia, ha de ser un n�mero natural.
     * @return {number} x elevat a la pot�ncia de n.
     */
    function pow(x, n) {
      ...
    }
    ```
	
	Aquest tipus de comentaris ens permeten entendre la finalitat de la funci� i com utilitzar-la de la manera correcta sense mirar el codi.
	Per cert, molts editors com [WebStorm](https://www.jetbrains.com/webstorm/) tamb� els poden entendre i utilitzar-los per proveir auto complete i algun tipus de comprovaci� autom�tica del codi.
	
	Tamb� hi ha eines com [JSDoc 3](https://github.com/jsdoc3/jsdoc) que poden generar documentaci� en HTML a partir dels comentaris. Pots llegir m�s informaci� sobre JSDoc a <http://usejsdoc.org/>.
	
Per qu� el problema est� resolt d'aquesta manera?
: El que est� escrit �s important. Per� el que *no* est� escrit pot ser incl�s m�s important per entendre el que est� passant. Per qu� el problema est� resolt d'aquesta manera espec�fica? El codi no ens d�na cap resposta.

	Si hi han diferents maneres de resoldre el problema, per qu� aquesta? Especialment quan no �s la m�s obvia. 
	
	Sense aquest tipus de comentaris la seg�ent situaci� pot oc�rrer:
	1. Tu (o el teu company) obres el codi escrit ja fa un temps, i veus que �s "sub-optim".
	2. Penses: "Que ximple que vaig ser, i que intel�ligent  que s�c ara", i reescrius el codi utilitzant la "manera m�s obvia i correcta".
	3 ... El desig de reescriure era bo. Per� durant el proc�s et d�nes compte que la soluci� "m�s obvia" en realitat falla. Incl�s recordes vagament per qu�, perqu� ja ho vas provar fa temps. Retornes a la variant correcta, per� has perdut temps.
	
	Els comentaris que ens expliquen la soluci� s�n molt importants. Ens ajuden a continuar el desenvolupament de manera correcta.
	
Hi ha algunes caracter�stiques subtils del codi? A on s�n utilitzades?
: Si el codi t� alguna cosa subtil i contra intu�tiva, definitivament val la pena comentar-la.
=======
Describe the architecture
: Provide a high-level overview of components, how they interact, what's the control flow in various situations... In short -- the bird's eye view of the code. There's a special language [UML](http://wikipedia.org/wiki/Unified_Modeling_Language) to build high-level architecture diagrams explaining the code. Definitely worth studying.

Document function parameters and usage
: There's a special syntax [JSDoc](http://en.wikipedia.org/wiki/JSDoc) to document a function: usage, parameters, returned value.

For instance:
```js
/**
 * Returns x raised to the n-th power.
 *
 * @param {number} x The number to raise.
 * @param {number} n The power, must be a natural number.
 * @return {number} x raised to the n-th power.
 */
function pow(x, n) {
  ...
}
```

Such comments allow us to understand the purpose of the function and use it the right way without looking in its code.

By the way, many editors like [WebStorm](https://www.jetbrains.com/webstorm/) can understand them as well and use them to provide autocomplete and some automatic code-checking.

Also, there are tools like [JSDoc 3](https://github.com/jsdoc3/jsdoc) that can generate HTML-documentation from the comments. You can read more information about JSDoc at <http://usejsdoc.org/>.

Why is the task solved this way?
: What's written is important. But what's *not* written may be even more important to understand what's going on. Why is the task solved exactly this way? The code gives no answer.

    If there are many ways to solve the task, why this one? Especially when it's not the most obvious one.

    Without such comments the following situation is possible:
    1. You (or your colleague) open the code written some time ago, and see that it's "suboptimal".
    2. You think: "How stupid I was then, and how much smarter I'm now", and rewrite using the "more obvious and correct" variant.
    3. ...The urge to rewrite was good. But in the process you see that the "more obvious" solution is actually lacking. You even dimly remember why, because you already tried it long ago. You revert to the correct variant, but the time was wasted.

    Comments that explain the solution are very important. They help to continue development the right way.

Any subtle features of the code? Where they are used?
: If the code has anything subtle and counter-intuitive, it's definitely worth commenting.
>>>>>>> 3699f73b4ccb2a57ac5ef990d2687bf31ccf564c

## Resum

Un signe important d'un bon desenvolupador s�n els comentaris: la seva pres�ncia i fins i tot la seva abs�ncia.

Bons comentaris ens ajuden a mantenir el codi de manera correcta, tornar despr�s d'un temps i utilitzar-lo de manera eficient.

**Comenta aix�:**

- Arquitectura en general, punts de vista d'alt nivell.
- Utilitzaci� de funcions.
- Solucions importants, especialment quan no s�n les immediatament obvies.

**Evita comentaris:**

<<<<<<< HEAD
- Que ens expliquen "com funciona el codi" i "que �s el que fa".
- Escriu-los nom�s si �s impossible fer que el codi sigui simple i auto descriptiu fins al punt que no els necessiti.
=======
- That tell "how code works" and "what it does".
- Put them in only if it's impossible to make the code so simple and self-descriptive that it doesn't require them.
>>>>>>> 3699f73b4ccb2a57ac5ef990d2687bf31ccf564c

Els comentaris tamb� s�n utilitzats per eines de documentaci� autom�tica com JSDoc3: els llegeixen i generen documents en HTML (o documents en altres formats).
