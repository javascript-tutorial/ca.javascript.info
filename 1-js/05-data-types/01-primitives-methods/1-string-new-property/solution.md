
Intenta executar:

```js run
let str = "Hello";

str.test = 5; // (*)

alert(str.test);
```

Depenent de si tens `use strict` o no, el resultat pot ser:

1. `undefined` (mode no estricte)
2. un error (mode estricte)

<<<<<<< HEAD
Per què? Parem esment al que passa a la línia `(*)`:

1. Quan s'accedeix a una propietat de `str`, es crea un "objecte embolcall".
2. En mode estricte, escriure-hi és una error.
3. Alternativament, l'operació amb la propietat continua, l'objecte agafa la propietat `test`, però després d'això "l'objecte embolcall" desapareix.
=======
1. When a property of `str` is accessed, a "wrapper object" is created.
2. In strict mode, writing into it is an error.
3. Otherwise, the operation with the property is carried on, the object gets the `test` property, but after that the "wrapper object" disappears, so in the last line `str` has no trace of the property.
>>>>>>> ea7738bb7c3616bb51ff14ae3db2a2747d7888ff

Així, sense el mode estricte, en l'última línia no queda ni rastre de la propietat de  `str`. 

**Aquest exemple mostra clarament que els primitius no són objectes.** 

No poden emmagatzemar informació adicional. 