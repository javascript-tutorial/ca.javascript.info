# Introducció a JavaScript

Vegem què fa de JavaScript un llenguatge tan especial, què podem aconseguir amb ell, i quines altres tecnologies s'hi integren bé.

## Què és JavaScript?

*JavaScript* fou inicialment creat per a *"donar vida a les pàgines web"*.

Els programes escrits en aquest llenguatge s'anomenen *scripts*. Poden ser escrits directament al codi HTML d'una pàgina web i executar-se automàticament quan la pàgina es carrega.

Els scripts es proporcionen i s'executen com a text pla. No necessiten cap preparació especial o compilació per executar-se.

En aquest aspecte, JavaScript és molt diferent d'un altre llenguatge anomenat [Java](https://ca.wikipedia.org/wiki/Java_(llenguatge_de_programaci%C3%B3)).

```smart header="Per què <u>Java</u>Script?"
Quan JavaScript fou creat, tenia un altre nom: "LiveScript". Però Java era molt popular en aquella època, així que es decidí que posicionar un nou llenguatge com el "germà petit" de Java seria útil.

No obstant, a l'evolucionar, JavaScript esdevingué un llenguatge completament independent amb la seva pròpia especificació anomenada  [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript), i actualment no té cap tipus de relació amb Java.
```

Avui dia, JavaScript es pot executar no només al navegador, sinó també al servidor; de fet, pot ésser executat en qualsevol dispositiu que tingui un programa especial anomenat [motor de JavaScript](https://ca.wikipedia.org/wiki/Int%C3%A8rpret_JavaScript).

El navegador disposa d'un motor integrat, generalment anomenat "Màquina virtual de JavaScript".

Motors diferents tenen "noms en clau" (criptònims) diferents. Per exemple:

- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- en Chrome i Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- en Firefox.
- ...Hi ha altres noms en clau com "Trident" i "Chakra" per diferents versions d'IE, "ChakraCore" per Microsoft Edge, "Nitro" i "SquirrelFish" per Safari, etc.

Fóra bo mantenir en ment els termes anteriors perquè són àmpliament utilitzats en articles de desenvolupadors a Internet. També els emprarem aquí. Per exemple, si "la funcionalitat X és suportada per V8", llavors probablement funcioni a Chrome i Opera.

```smart header="Com funcionen els motors?"

Els motors són complicats, però els fonaments són fàcils.

1. El motor (en el cas dels navegadors, integrat) llegeix, o analitza ("parses") el script.
2. Posteriorment, converteix ("compiles") el script a llenguatge màquina.
3. Finalment, el codi màquina s'executa veloçment.

El motor aplica optimitzacions a cada pas del procés. Fins i tot supervisa l'script compilat mentre s'executa, analitza les dades que rep i retorna, i aplica optimitzacions al codi màquina basant-se en aquest coneixement. Quan això passa, els scripts s'executen força ràpid.
```

## Què pot fer JavaScript al navegador?

El JavaScript modern és un llenguatge de programació "segur". No ofereix accés de baix nivell a la memòria o la CPU, ja que fou inicialment creat per navegadors que no ho requerien.

Les capacitats de JavaScript depenen majoritàriament de l'entorn on s'executa. Per exemple, [Node.js](https://wikipedia.org/wiki/Node.js) suporta funcions que permeten, amb JavaScript, llegir i escriure fitxers, realitzar peticions a través de la xarxa, etc.

Al navegador, JavaScript té capacitat de manipulació de la pàgina web, d'interacció amb l'usuari, i amb el servidor web.

A tall d'exemple, JavaScript en navegador és capaç de:

- Afegir nous components HTML a la pàgina, alterar el contingut existent, modificar estils.
- Respondre a les accions de l'usuari, com clics del ratolí, moviments del punter, o bé al prémer tecles.
- Enviar peticions a servidors remots a través de la xarxa, descarregar i carregar fitxers (també anomenades tecnologies [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) i [COMET](https://en.wikipedia.org/wiki/Comet_(programming))).
- Obtenir i definir galetes ("cookies"), enviar qüestions a l'usuari, mostrar missatges.
- Emmagatzemar dades al dispositiu del client ("local storage", emmagatzematge local).

## Què NO pot fer JavaScript al navegador?

Les capacitats de JavaScript al navegador són limitades per protegir a l'usuari. L'objectiu és evitar el robatori d'informació privada o la corrupció de les dades de l'usuari per part d'una pàgina web maliciosa.

Com a mostra, algunes d'aquestes restriccions són:

- El codi JavaScript d'una pàgina web no pot llegir o escriure fitxers arbitraris al disc dur, copiar-los o executar programes. No té accés directe a funcions del sistema operatiu.

    Els navegadors moderns permeten treballar amb fitxers, però l'accés és limitat i només es garanteix si l'usuari realitza certes accions, com "soltar" (amb drag-and-drop) un fitxer a la finestra del navegador, o si el selecciona amb una etiqueta `<input>`.

    Hi ha maneres d'interactuar amb la càmera/micròfon o altres dispositius, però requereixen el permís explícit de l'usuari. Així, una pàgina web amb JavaScript no pot activar la càmera sigil·losament, observar l'escena i enviar la informació a la [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Les diferents pestanyes o finestres, generalment, no saben res de les altres. A vegades en saben alguna cosa, com quan una finestra empra JavaScript per obrir-ne una altra, però fins i tot en aquest cas el codi JavaScript d'una pàgina no pot accedir el codi de l'altra si provenen de llocs diferents (domini, protocol o port diferent).

    Això s'anomena "Same Origin Policy" (Política del Mateix Origen). Per evitar-ho, *ambdues pàgines* han d'acceptar l'intercanvi de dades i contenir un codi JavaScript especial que el gestionarà. Ho veurem més endavant.

    Aquesta limitació és, també, per la seguretat de l'usuari. Una pàgina de `http://anysite.com` que ha obert un usuari no ha de poder accedir a una altra pestanya amb la URL `http://gmail.com` i robar-hi informació.
- JavaScript pot comunicar-se fàcilment a través d'internet amb el servidor d'on prové la pàgina, però llur capacitat per rebre dades d'altres llocs o dominis està bloquejada. Tot i que és possible, requereix l'aprovació explícita (expressada a les capçaleres HTTP) del lloc remot. Això, un cop més, és una limitació per seguretat.

![](limitations.svg)

Aquests límits desapareixen si JavaScript s'empra fora del navegador (en un servidor, per exemple). Els navegadors moderns també permeten plug-ins o extensions que poden demanar permisos addicionals.

## Què fa JavaScript únic?

JavaScript té, com a mínim, *tres* punts forts:

```compare
+ Integració completa amb HTML/CSS.
+ Les coses simples es fan de forma simple
+ És suportat per tots els navegadors importants i està activat per defecte.
```
JavaScript és l'única tecnologia de navegador que combina aquestes tres característiques.

Això és el que fa JavaScript únic. Per això és l'eina més estesa per crear interfícies de navegador.

Quan es valora aprendre una nova tecnologia, és recomanable comprovar les perspectives d'aquesta: per tant, procedim a comentar les tendències que l'afectaran properament, incloent nous llenguatges i capacitats dels navegadors.


## Llenguatges "sobre" JavaScript

La sintaxi de JavaScript no satisfà les necessitats de tothom. Diferents persones volen diferents funcionalitats.

Això és esperable, ja que els projectes i requisits depenen de cadascú.

Recentment, ha aparegut una plètora de llenguatges nous, que es *transpilen* (converteixen) a JavaScript abans d'executar-se al navegador.

Les noves eines fan que la conversió sigui ràpida i transparent, permetent als desenvolupadors programar en un altre llenguatge i convertir-lo automàticament.

Alguns exemples d'aquests llenguatges:

- [CoffeeScript](http://coffeescript.org/) és "syntactic sugar" per JavaScript. Introdueix sintaxi més curta, permetent escriure codi més clar i precís. Generalment, els devs de Ruby se l'estimen força.
- [TypeScript](http://www.typescriptlang.org/) se centra en afegir "tipatge estricte" per simplificar el desenvolupament i manteniment de sistemes complexos. És desenvolupat per Microsoft.
- [Dart](https://www.dartlang.org/) és un llenguatge independent, amb el seu propi motor, que s'executa en entorns diferents del navegador (com les aplicacions mòbils). Originalment, Google l'oferí com a substitut de JavaScript, però actualment els navegadors requereixen que es converteixi a JavaScript, com els llenguatges anteriors.

N'hi ha més. Per suposat, fins i tot emprant algun d'aquests llenguatges, hom hauria de conèixer JavaScript per tal d'entendre realment què està fent.

## Resum

- JavaScript fou inicialment creat com un llenguatge per a navegadors, però actualment s'empra també en altres entorns.
- Avui dia, JavaScript ostenta indiscutiblement el títol del llenguatge de navegador amb integració completa amb HTML/CSS més utilitzat.
- Hi ha diversos llenguatges que es "converteixen" a JavaScript i proporcionen certes funcionalitats. Es recomana donar-los un cop d'ull, almenys breument, un cop dominat JavaScript.
