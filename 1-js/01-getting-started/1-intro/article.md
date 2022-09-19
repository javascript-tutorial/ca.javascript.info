# Introducció a JavaScript

<<<<<<< HEAD
Vegem què fa de JavaScript un llenguatge tan especial, què podem aconseguir amb ell, i quines altres tecnologies s'hi integren bé.
=======
Let's see what's so special about JavaScript, what we can achieve with it, and what other technologies play well with it.
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8

## Què és JavaScript?

<<<<<<< HEAD
*JavaScript* fou inicialment creat per a *"donar vida a les pàgines web"*.
=======
*JavaScript* was initially created to "make web pages alive".
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8

Els programes escrits en aquest llenguatge s'anomenen *scripts*. Poden ser escrits directament al codi HTML d'una pàgina web i executar-se automàticament quan la pàgina es carrega.

Els scripts es proporcionen i s'executen com a text pla. No necessiten cap preparació especial o compilació per executar-se.

En aquest aspecte, JavaScript és molt diferent d'un altre llenguatge anomenat [Java](https://ca.wikipedia.org/wiki/Java_(llenguatge_de_programaci%C3%B3)).

<<<<<<< HEAD
```smart header="Per què <u>Java</u>Script?"
Quan JavaScript fou creat, tenia un altre nom: "LiveScript". Però Java era molt popular en aquella època, així que es decidí que posicionar un nou llenguatge com el "germà petit" de Java seria útil.
=======
```smart header="Why is it called <u>Java</u>Script?"
When JavaScript was created, it initially had another name: "LiveScript". But Java was very popular at that time, so it was decided that positioning a new language as a "younger brother" of Java would help.
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8

No obstant, a l'evolucionar, JavaScript esdevingué un llenguatge completament independent amb la seva pròpia especificació anomenada  [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript), i actualment no té cap tipus de relació amb Java.
```

Avui dia, JavaScript es pot executar no només al navegador, sinó també al servidor; de fet, pot ésser executat en qualsevol dispositiu que tingui un programa especial anomenat [motor de JavaScript](https://ca.wikipedia.org/wiki/Int%C3%A8rpret_JavaScript).

El navegador disposa d'un motor integrat, generalment anomenat "Màquina virtual de JavaScript".

Motors diferents tenen "noms en clau" (criptònims) diferents. Per exemple:

<<<<<<< HEAD
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- en Chrome i Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- en Firefox.
- ...Hi ha altres noms en clau com "Trident" i "Chakra" per diferents versions d'IE, "ChakraCore" per Microsoft Edge, "Nitro" i "SquirrelFish" per Safari, etc.

Fóra bo mantenir en ment els termes anteriors perquè són àmpliament utilitzats en articles de desenvolupadors a Internet. També els emprarem aquí. Per exemple, si "la funcionalitat X és suportada per V8", llavors probablement funcioni a Chrome i Opera.
=======
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- in Chrome, Opera and Edge.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- in Firefox.
- ...There are other codenames like "Chakra" for IE, "JavaScriptCore", "Nitro" and "SquirrelFish" for Safari, etc.

The terms above are good to remember because they are used in developer articles on the internet. We'll use them too. For instance, if "a feature X is supported by V8", then it probably works in Chrome, Opera and Edge.
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8

```smart header="Com funcionen els motors?"

Els motors són complicats, però els fonaments són fàcils.

<<<<<<< HEAD
1. El motor (en el cas dels navegadors, integrat) llegeix, o analitza ("parses") el script.
2. Posteriorment, converteix ("compiles") el script a llenguatge màquina.
3. Finalment, el codi màquina s'executa veloçment.

El motor aplica optimitzacions a cada pas del procés. Fins i tot supervisa l'script compilat mentre s'executa, analitza les dades que rep i retorna, i aplica optimitzacions al codi màquina basant-se en aquest coneixement. Quan això passa, els scripts s'executen força ràpid.
=======
1. The engine (embedded if it's a browser) reads ("parses") the script.
2. Then it converts ("compiles") the script to machine code.
3. And then the machine code runs, pretty fast.

The engine applies optimizations at each step of the process. It even watches the compiled script as it runs, analyzes the data that flows through it, and further optimizes the machine code based on that knowledge.
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8
```

## Què pot fer JavaScript al navegador?

<<<<<<< HEAD
El JavaScript modern és un llenguatge de programació "segur". No ofereix accés de baix nivell a la memòria o la CPU, ja que fou inicialment creat per navegadors que no ho requerien.
=======
Modern JavaScript is a "safe" programming language. It does not provide low-level access to memory or the CPU, because it was initially created for browsers which do not require it.
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8

Les capacitats de JavaScript depenen majoritàriament de l'entorn on s'executa. Per exemple, [Node.js](https://wikipedia.org/wiki/Node.js) suporta funcions que permeten, amb JavaScript, llegir i escriure fitxers, realitzar peticions a través de la xarxa, etc.

Al navegador, JavaScript té capacitat de manipulació de la pàgina web, d'interacció amb l'usuari, i amb el servidor web.

A tall d'exemple, JavaScript en navegador és capaç de:

- Afegir nous components HTML a la pàgina, alterar el contingut existent, modificar estils.
- Respondre a les accions de l'usuari, com clics del ratolí, moviments del punter, o bé al prémer tecles.
- Enviar peticions a servidors remots a través de la xarxa, descarregar i carregar fitxers (també anomenades tecnologies [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) i [COMET](https://en.wikipedia.org/wiki/Comet_(programming))).
- Obtenir i definir galetes ("cookies"), enviar qüestions a l'usuari, mostrar missatges.
- Emmagatzemar dades al dispositiu del client ("local storage", emmagatzematge local).

## Què NO pot fer JavaScript al navegador?

<<<<<<< HEAD
Les capacitats de JavaScript al navegador són limitades per protegir a l'usuari. L'objectiu és evitar el robatori d'informació privada o la corrupció de les dades de l'usuari per part d'una pàgina web maliciosa.
=======
JavaScript's abilities in the browser are limited to protect the user's safety. The aim is to prevent an evil webpage from accessing private information or harming the user's data.
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8

Com a mostra, algunes d'aquestes restriccions són:

<<<<<<< HEAD
- El codi JavaScript d'una pàgina web no pot llegir o escriure fitxers arbitraris al disc dur, copiar-los o executar programes. No té accés directe a funcions del sistema operatiu.
=======
- JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs. It has no direct access to OS functions.
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8

    Els navegadors moderns permeten treballar amb fitxers, però l'accés és limitat i només es garanteix si l'usuari realitza certes accions, com "soltar" (amb drag-and-drop) un fitxer a la finestra del navegador, o si el selecciona amb una etiqueta `<input>`.

<<<<<<< HEAD
    Hi ha maneres d'interactuar amb la càmera/micròfon o altres dispositius, però requereixen el permís explícit de l'usuari. Així, una pàgina web amb JavaScript no pot activar la càmera sigil·losament, observar l'escena i enviar la informació a la [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Les diferents pestanyes o finestres, generalment, no saben res de les altres. A vegades en saben alguna cosa, com quan una finestra empra JavaScript per obrir-ne una altra, però fins i tot en aquest cas el codi JavaScript d'una pàgina no pot accedir el codi de l'altra si provenen de llocs diferents (domini, protocol o port diferent).

    Això s'anomena "Same Origin Policy" (Política del Mateix Origen). Per evitar-ho, *ambdues pàgines* han d'acceptar l'intercanvi de dades i contenir un codi JavaScript especial que el gestionarà. Ho veurem més endavant.

    Aquesta limitació és, també, per la seguretat de l'usuari. Una pàgina de `http://anysite.com` que ha obert un usuari no ha de poder accedir a una altra pestanya amb la URL `http://gmail.com` i robar-hi informació.
- JavaScript pot comunicar-se fàcilment a través d'internet amb el servidor d'on prové la pàgina, però llur capacitat per rebre dades d'altres llocs o dominis està bloquejada. Tot i que és possible, requereix l'aprovació explícita (expressada a les capçaleres HTTP) del lloc remot. Això, un cop més, és una limitació per seguretat.

![](limitations.svg)

Aquests límits desapareixen si JavaScript s'empra fora del navegador (en un servidor, per exemple). Els navegadors moderns també permeten plug-ins o extensions que poden demanar permisos addicionals.
=======
    There are ways to interact with the camera/microphone and other devices, but they require a user's explicit permission. So a JavaScript-enabled page may not sneakily enable a web-camera, observe the surroundings and send the information to the [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Different tabs/windows generally do not know about each other. Sometimes they do, for example when one window uses JavaScript to open the other one. But even in this case, JavaScript from one page may not access the other page if they come from different sites (from a different domain, protocol or port).

    This is called the "Same Origin Policy". To work around that, *both pages* must agree for data exchange and must contain special JavaScript code that handles it. We'll cover that in the tutorial.

    This limitation is, again, for the user's safety. A page from `http://anysite.com` which a user has opened must not be able to access another browser tab with the URL `http://gmail.com`, for example, and steal information from there.
- JavaScript can easily communicate over the net to the server where the current page came from. But its ability to receive data from other sites/domains is crippled. Though possible, it requires explicit agreement (expressed in HTTP headers) from the remote side. Once again, that's a safety limitation.

![](limitations.svg)

Such limitations do not exist if JavaScript is used outside of the browser, for example on a server. Modern browsers also allow plugins/extensions which may ask for extended permissions.
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8

## Què fa JavaScript únic?

JavaScript té, com a mínim, *tres* punts forts:

```compare
<<<<<<< HEAD
+ Integració completa amb HTML/CSS.
+ Les coses simples es fan de forma simple
+ És suportat per tots els navegadors importants i està activat per defecte.
=======
+ Full integration with HTML/CSS.
+ Simple things are done simply.
+ Supported by all major browsers and enabled by default.
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8
```
JavaScript és l'única tecnologia de navegador que combina aquestes tres característiques.

Això és el que fa JavaScript únic. Per això és l'eina més estesa per crear interfícies de navegador.

<<<<<<< HEAD
Quan es valora aprendre una nova tecnologia, és recomanable comprovar les perspectives d'aquesta: per tant, procedim a comentar les tendències que l'afectaran properament, incloent nous llenguatges i capacitats dels navegadors.

=======
That said, JavaScript can be used to create servers, mobile applications, etc.
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8

## Llenguatges "sobre" JavaScript

La sintaxi de JavaScript no satisfà les necessitats de tothom. Diferents persones volen diferents funcionalitats.

Això és esperable, ja que els projectes i requisits depenen de cadascú.

<<<<<<< HEAD
Recentment, ha aparegut una plètora de llenguatges nous, que es *transpilen* (converteixen) a JavaScript abans d'executar-se al navegador.
=======
So, recently a plethora of new languages appeared, which are *transpiled* (converted) to JavaScript before they run in the browser.
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8

Les noves eines fan que la conversió sigui ràpida i transparent, permetent als desenvolupadors programar en un altre llenguatge i convertir-lo automàticament.

Alguns exemples d'aquests llenguatges:

<<<<<<< HEAD
- [CoffeeScript](http://coffeescript.org/) és "syntactic sugar" per JavaScript. Introdueix sintaxi més curta, permetent escriure codi més clar i precís. Generalment, els devs de Ruby se l'estimen força.
- [TypeScript](http://www.typescriptlang.org/) se centra en afegir "tipatge estricte" per simplificar el desenvolupament i manteniment de sistemes complexos. És desenvolupat per Microsoft.
- [Dart](https://www.dartlang.org/) és un llenguatge independent, amb el seu propi motor, que s'executa en entorns diferents del navegador (com les aplicacions mòbils). Originalment, Google l'oferí com a substitut de JavaScript, però actualment els navegadors requereixen que es converteixi a JavaScript, com els llenguatges anteriors.

N'hi ha més. Per suposat, fins i tot emprant algun d'aquests llenguatges, hom hauria de conèixer JavaScript per tal d'entendre realment què està fent.
=======
- [CoffeeScript](https://coffeescript.org/) is "syntactic sugar" for JavaScript. It introduces shorter syntax, allowing us to write clearer and more precise code. Usually, Ruby devs like it.
- [TypeScript](https://www.typescriptlang.org/) is concentrated on adding "strict data typing" to simplify the development and support of complex systems. It is developed by Microsoft.
- [Flow](https://flow.org/) also adds data typing, but in a different way. Developed by Facebook.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript. Developed by Google.
- [Brython](https://brython.info/) is a Python transpiler to JavaScript that enables the writing of applications in pure Python without JavaScript.
- [Kotlin](https://kotlinlang.org/docs/reference/js-overview.html) is a modern, concise and safe programming language that can target the browser or Node.

There are more. Of course, even if we use one of these transpiled languages, we should also know JavaScript to really understand what we're doing.
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8

## Resum

<<<<<<< HEAD
- JavaScript fou inicialment creat com un llenguatge per a navegadors, però actualment s'empra també en altres entorns.
- Avui dia, JavaScript ostenta indiscutiblement el títol del llenguatge de navegador amb integració completa amb HTML/CSS més utilitzat.
- Hi ha diversos llenguatges que es "converteixen" a JavaScript i proporcionen certes funcionalitats. Es recomana donar-los un cop d'ull, almenys breument, un cop dominat JavaScript.
=======
- JavaScript was initially created as a browser-only language, but it is now used in many other environments as well.
- Today, JavaScript has a unique position as the most widely-adopted browser language, fully integrated with HTML/CSS.
- There are many languages that get "transpiled" to JavaScript and provide certain features. It is recommended to take a look at them, at least briefly, after mastering JavaScript.
>>>>>>> 53b35c16835b7020a0a5046da5a47599d313bbb8
