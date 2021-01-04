# Hola, món!

<<<<<<< HEAD
El tutorial que esteu llegint versa sobre el nucli de JavaScript, que és independent de la plataforma. Més endavant, aprendreu sobre Node.js i altres plataformes que l'empren.
=======
This part of the tutorial is about core JavaScript, the language itself.
>>>>>>> 039716de8a96f49b5fccd7aed5effff2e719dfe5

Però necessitem un entorn de treball per executar els scripts i, com aquest llibre és en línia, el navegador és una bona opció. Mantindrem la quantitat mínima de comandes específiques del navegador (com `alert`) perquè no pergueu temps si planegeu centrar-vos en un altre entorn (com Node.js). Ens centrarem en JavaScript al navegador en la [propera part](/ui) del tutorial.

Per començar, vegem com afegir un script a una pàgina web. Per entorns en servidor (com Node.js), podeu executar un script amb una comanda com `"node my.js"`.


## L'etiqueta "script"

<<<<<<< HEAD
Els programes JavaScript poden inserir-se a qualsevol part d'un document HTML mitjançant l'etiqueta `<script>`.
=======
JavaScript programs can be inserted almost anywhere into an HTML document using the `<script>` tag.
>>>>>>> 039716de8a96f49b5fccd7aed5effff2e719dfe5

Per exemple:

```html run height=100
<!DOCTYPE HTML>
<html>

<body>

  <p>Abans del script...</p>

*!*
  <script>
    alert( 'Hola, món!' );
  </script>
*/!*

  <p>...Després del script.</p>

</body>

</html>
```

```online
Podeu executar l'exemple fent clic al botó "Play" de la cantonada superior dreta del requadre superior.
```

L'etiqueta `<script>` conté codi JavaScript que s'executa automàticament quan el navegador processa l'etiqueta.


## Etiquetatge modern

L'etiquta `<script>` té alguns atributs poc emprats avui dia però que encara es poden trobar a codi antic:

<<<<<<< HEAD
L'atribut `type`: <code>&lt;script <u>type</u>=...&gt;</code>
: L'antic estàndard de HTML, HTML4, requeria que un script tingués un `type`. Normalment era `type="text/javascript"`. Ara ja no fa falta. També cal dir que HTML5, l'estàndard modern de HTML, canvià per complet el significat d'aquest atribut. Actualment, es pot emprar pels mòduls de JavaScript. Això, però, és un tema avançat; parlarem sobre mòduls en un altre apartat del tutorial.
=======
The `type` attribute: <code>&lt;script <u>type</u>=...&gt;</code>
: The old HTML standard, HTML4, required a script to have a `type`. Usually it was `type="text/javascript"`. It's not required anymore. Also, the modern HTML standard totally changed the meaning of this attribute. Now, it can be used for JavaScript modules. But that's an advanced topic, we'll talk about modules in another part of the tutorial.
>>>>>>> 039716de8a96f49b5fccd7aed5effff2e719dfe5

L'atribut `language`: <code>&lt;script <u>language</u>=...&gt;</code>
: Aquest atribut pretenia mostrar el llenguatge del script; la seva existència ja no té sentit perquè JavaScript és el llenguatge per defecte. No hi ha necessitat de fer-lo servir.

Comentaris abans i després de scripts.
: A llibres i guies molt antics, podeu trobar comentaris dins d'etiquetes `<script>`, com aquests:

    ```html no-beautify
    <script type="text/javascript"><!--
        ...
    //--></script>
    ```

<<<<<<< HEAD
    Aquest truc no es fa servir en JavaScript modern. Aquests comentaris ocultaven codi JavaScript pels navegadors antics que no sabien com processar les etiquetes `<script>`. Com els navegadors dels últims 15 anys no tenen aquest problema, aquest tipus de comentari us pot ajudar a identificar codi ben antic.
=======
    This trick isn't used in modern JavaScript. These comments hide JavaScript code from old browsers that didn't know how to process the `<script>` tag. Since browsers released in the last 15 years don't have this issue, this kind of comment can help you identify really old code.
>>>>>>> 039716de8a96f49b5fccd7aed5effff2e719dfe5


## Scripts externs

Si tenim molt de codi JavaScript, podem posar-lo a un fitxer separat.

Els fitxers de script s'inclouen a l'HTML amb l'atribut `src`:

```html
<script src="/ruta/al/script.js"></script>
```

<<<<<<< HEAD
Aquí, `/ruta/al/script.js` és una ruta absoluta al fitxer script (des de l'arrel del lloc).

També podeu proporcionar una ruta relativa des de la pàgina actual. Per il·lustrar, `src="script.js"` faria referència a un fitxer `"script.js"` en el directori actual.
=======
Here, `/path/to/script.js` is an absolute path to the script from the site root. One can also provide a relative path from the current page. For instance, `src="script.js"` would mean a file `"script.js"` in the current folder.
>>>>>>> 039716de8a96f49b5fccd7aed5effff2e719dfe5

També podem introduir una URL sencera. Per exemple:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js"></script>
```

Per incloure múltiples scripts, empreu múltiples etiquetes:

```html
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
…
```

```smart
Com a normal, només s'inclouen dins l'HTML els scripts més simples. Els més complexos romanen com a fitxers separats.

L'avantatge d'un fitxer separat és que el navegador el descarregarà i el desarà a la seva memòria [cau](https://en.wikipedia.org/wiki/Web_cache).

Altres pàgines que referencien el mateix script l'obtindran de la memòria cau en lloc de descarregar-lo, així que el fitxer realment només es descarrega un cop.

Això redueix el tràfic web i fa les pàgines més ràpides.
```

````warn header="Si `src` està definit, el contingut del script és ignorat."
Una etiqueta `<script>` no pot tenir l'etiqueta `src` i contenir codi alhora.

Això no funcionarà:

```html
<script *!*src*/!*="file.js">
  alert(1); // el contingut s'ignora perquè src està definit
</script>
```

Hem de triar o bé un `<script src="…">` extern o bé un `<script>` normal amb codi.

L'exemple anterior es pot dividir en dos scripts perquè funcioni:

```html
<script src="file.js"></script>
<script>
  alert(1);
</script>
```
````

## Resum

- Podem emprar una etiqueta `<script>` per afegir codi JavaScript a una pàgina web.
- Els atributs `type` i `language` no són necessaris.
- Podem inserir un script d'un fitxer extern amb `<script src="ruta/al/script.js"></script>`.


Hi ha molts més per aprendre sobre scripts de navegador i llur interacció amb la pàgina web. Però cal tenir en ment que aquesta part del tutorial versa sobre el llenguatge JavaScript, així que no ens hauríem de distreure comentant implementacions específiques d'aquest per navegadors. Emprarem el navegador com una forma d'executar JavaScript, molt convenient per quan llegim en línia, però cal recordar que és només una opció entre d'altres.
