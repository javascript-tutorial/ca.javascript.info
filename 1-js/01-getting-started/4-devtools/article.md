# La consola de desenvolupador

El codi és propens a contenir errors. Segurament cometreu errors... perdó, *i tant* que cometreu errors, almenys si sou humà i no un [robot](https://en.wikipedia.org/wiki/Bender_(Futurama)).

Al navegador, però, per defecte els usuaris no veuen errors. Per tant, si alguna cosa falla, no podrem veure què està trencat i no ho podrem arreglar.

Per veure errors i obtenir molta més informació útil sobre els scripts, s'han incorporat les "eines de desenvolupador" als navegadors.

La majoria de desenvolupadors tendeixen a fer servir Chrome o Firefox per desenvolupar perquè aquests navegadors tenen les millors eines de desenvolupador. Altres navegadors també proporcionen eines de desenvolupador, a vegades amb funcions especials, però acostumen a anar a rebuf de Chrome/Firefox. Així, la majoria dels desenvolupadors tenen un navegador "preferit" i canvien a un altre si el problema és específic d'un navegador concret.

Les eines de desenvolupador són potents; tenen diverses característiques. Per començar, aprendrem com obrir-les, veure errors, i executar comandes de JavaScript.

## Google Chrome

Obriu la pàgina [bug.html](bug.html).

Hi ha un error al codi JavaScript de la pàgina. Es troba amagat als ulls d'un visitant comú, així que obrirem les eines de desenvolupador per veure'l.

Premeu `key:F12` o, si feu servir Mac, llavors `key:Cmd+Opt+J`.

Les eines de desenvolupador s'obriran amb la pestanya de Consola per defecte.

It looks somewhat like this:

![chrome](chrome.png)

L'aparença exacta de les eines de desenvolupador depenen de la vostra versió del Chrome. Canvia de tant en tant però hauria de ser similar.

- Aquí podem veure el missatge d'error, ressaltat en vermell. En aquest cas, l'script conté una comanda desconeguda "lalala".
- A la dreta, hi ha un enllaç clicable al codi font `bug.html:12` amb el número de línia on ha ocorregut l'error.

<<<<<<< HEAD:1-js/01-getting-started/3-devtools/article.md
Sota el missatge d'error, hi ha un símbol blau `>`. Marca la "línia de comandes" on podem escriure comandes JavaScript. Premeu `key:Enter` per executar-les (`key:Shift+Enter` per escriure comandes multilínia).
=======
Below the error message, there is a blue `>` symbol. It marks a "command line" where we can type JavaScript commands. Press `key:Enter` to run them.
>>>>>>> 2efe0dce18a57f2b6121ed6656d6fe10b0ee8f96:1-js/01-getting-started/4-devtools/article.md

Ara podem veure els errors, i això és suficient per començar. Revisitarem les eines de desenvolupador més endavant i estudiarem la depuració de codi més en profunditat al capítol <info:debugging-chrome>.

```smart header="Multi-line input"
Usually, when we put a line of code into the console, and then press `key:Enter`, it executes.

To insert multiple lines, press `key:Shift+Enter`. This way one can enter long fragments of JavaScript code.
```

## Firefox, Edge, i altres

La majoria de navegadors fa servir la tecla `key:F12` per obrir les eines de desenvolupador.

L'aparença de les eines és força similar. Un cop s'aprèn a utilitzar-ne una (podeu començar amb Chrome), es pot saltar fàcilment a una altra.

## Safari

Safari (navegador de Mac, no suportat a Windows/Linux) és una mica especial. Primer s'ha d'activar el "Menú de desenvolupador".

Obriu Preferències i aneu al panell "Avançat". Hi ha una casella al final:

![safari](safari.png)

Ara `key:Cmd+Opt+C` pot mostrar i ocultar la consola. Noteu que ha aparegut un nou element al menú superior anomenat "Desenvolupador". Té diverses comandes i opcions.

<<<<<<< HEAD:1-js/01-getting-started/3-devtools/article.md
## Entrada de més d'una línia

Normalment, quan entrem una línia de codi a la consola, i premem `key:Enter`, s'executa.

Per inserir més d'una línia, premeu `key:Shift+Enter`.

## Resum
=======
## Summary
>>>>>>> 2efe0dce18a57f2b6121ed6656d6fe10b0ee8f96:1-js/01-getting-started/4-devtools/article.md

- Les eines de desenvolupador ens permeten veure errors, executar comandes, examinar les variables, i moltes més coses.
- Es poden obrir amb la tecla `key:F12` a la majoria de navegadors amb Windows. Chrome per Mac necessita `key:Cmd+Opt+J`, Safari: `key:Cmd+Opt+C` (primer s'ha d'activar).

Ara tenim l'entorn preparat. A la propera secció, ens endinsarem en JavaScript.
