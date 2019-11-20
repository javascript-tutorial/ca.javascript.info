# Entorn del navegador, especificacions

JavaScript es va crear inicialment per a navegadors web. Des d’aleshores, ha evolucionat i s’ha convertit en un idioma amb molts usos i plataformes.

Una plataforma pot ser un navegador, un servidor web, una rentadora, o un altre *host*. Cadascun d'ells ofereix una funcionalitat específica a la plataforma. L'especificació JavaScript l'anomena *host environment*.

Un *host environment* proporciona objectes i funcions específiques de la plataforma addicionals al nucli del llenguatge. Els navegadors web proporcionen un mitjà per controlar les pàgines web. Node.js proporciona funcions del servidor, i així, successivament.

A continuació s'explica el que passa quan JavaScript funciona en un navegador web:

![](windowObjects.svg)

Hi ha un objecte "arrel" anomenat `window`. Té dos papers:

1. En primer lloc, és un objecte global per al codi JavaScript, tal com es descriu al capítol <info:global-object>.
2. En segon lloc, representa la "browser window" i proporciona mètodes per controlar-la.

Per exemple, aquí el fem servir com a objecte global:

```js run
function sayHi() {
  alert("Hello");
}

// Les funcions globals són accessibles com a propietats de la finestra (window)
window.sayHi();
```

I aquí la fem servir com a finestra del navegador, per veure l'alçada de la finestra (window):

```js run
alert(window.innerHeight); // inner window height
```

Hi ha més mètodes i propietats específiques per les finestres, les veurem més endavant.

## Document Object Model (DOM)

L’objecte `document` dóna accés al contingut de la pàgina. Podem canviar o crear qualsevol cosa de la pàgina utilitzant-lo.

Per exemple:
```js run
// canvia el color de fons per vermell
document.body.style.background = "red";

// es canvia de nou al cap d’un segon
setTimeout(() => document.body.style.background = "", 1000);
```

Aquí hem utilitzat `document.body.style`, però hi ha molt, molt més. Les propietats i els mètodes es descriuen a l'especificació. Hi ha dos grups de treball que el desenvolupen:

1. [W3C](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium) -- la documentació és a <https://www.w3.org/TR/dom>.
2. [WhatWG](https://en.wikipedia.org/wiki/WHATWG), publicant a <https://dom.spec.whatwg.org>.

I com sol passar, els dos grups no sempre estan d’acord, de manera que és com si tinguéssim dos conjunts estàndards. Però són molt similars i, eventualment, les coses es fusionen. La documentació que podeu trobar als recursos donats és molt similar, amb un 99% aproximat. Hi ha diferències molt petites que probablement ni us adonareu.

Personalment, em sembla <https://dom.spec.whatwg.org> més agradable d'utilitzar.

En l'edat antiga, no hi havia cap estàndard en absolut, cada navegador implementava com els hi semblava. Els diferents navegadors tenien diferents configuracions, mètodes i propietats per a la mateixa cosa, i els desenvolupadors havien d’escriure codi diferent per a cadascun d’ells. Temps foscos i desordenats.

Fins i tot ara de vegades podem trobar codi antic que utilitza propietats específiques del navegador i funciona amb incompatibilitats. Però, en aquest tutorial utilitzarem coses modernes: no cal que aprenguem coses antigues fins que no es necessiten realment (les probabilitats són altes que no sigui necessari).

Aleshores va aparèixer l’estàndard DOM, per intentar que tothom s'entengués. La primera versió va ser "DOM Nivell 1", després es va ampliar a DOM Nivell 2, després DOM Nivell 3 i ara ja s'ha arribat a DOM Nivell 4. La gent del grup WhatWG es va cansar dels números de versió i diuen només "DOM", sense número. Així que farem el mateix.

```smart header="DOM no només és per a navegadors"
L’especificació DOM explica l’estructura d’un document i proporciona objectes per manipular-lo. Hi ha instruments que no són de navegador que també l’utilitzen.

Per exemple, les eines del servidor que descarreguen pàgines HTML i les processen utilitzen el DOM. Tanmateix, només poden donar suport a una part de l'especificació.
```

```smart header="CSSOM per l'estil"
Les regles i fulls d'estils CSS no estan estructurats com HTML. Hi ha una especificació per separat [CSSOM] (https://www.w3.org/TR/cssom-1/) que explica com es representen com a objectes i com s'han de llegir i escriure.

CSSOM s'utilitza juntament amb DOM quan modifiquem les regles d'estil del document. Tanmateix, en la pràctica, rarament es requereix CSSOM, perquè normalment les regles CSS són estàtiques. Rarament cal afegir o treure les regles CSS de JavaScript, de manera que no ho cobrirem ara mateix.
```

## BOM (part de les especificacions HTML)

El Browser Object Model (BOM) són objectes addicionals proporcionats pel navegador (host environment) per treballar amb tot, excepte el document.

Per exemple:

- L'objecte [navigator](mdn:api/Window/navigator) proporciona informació de fons sobre el navegador i el sistema operatiu. Hi ha moltes propietats, però les dues més conegudes són: `navigator.userAgent` -- sobre el navegador actual i `navigator.platform` -- sobre la plataforma (pot ajudar diferenciar entre Windows/Linux/Mac, etc.).
- L'objecte [location](mdn:api/Window/location) permet llegir l’URL actual i es pot redirigir el navegador cap a una nova URL.

A continuació, es mostra com podem fer servir l'objecte `location`:

```js run
alert(location.href); // mostra URL actual
if (confirm("Go to wikipedia?")) {
  location.href = "https://wikipedia.org"; // redirigeix el navegador a una URL diferent
}
```

Les funcions `alert/confirm/prompt` també formen part de la BOM: no estan directament relacionades amb el document, sinó que representen mètodes purs del navegador per comunicar-se amb l'usuari.

```smart header="Especificació HTML"
El BOM és la part general de l'[especificació HTML](https://html.spec.whatwg.org).

Sí, ho has sentit bé. L'especificació HTML de <https://html.spec.whatwg.org> no només es refereix al "llenguatge HTML" (etiquetes, atributs), sinó que també abasta un munt d'objectes, mètodes i extensions DOM específiques del navegador. Això és "HTML en termes amplis".
```

## Resum

Parlant d'estàndards, tenim:

Especificació DOM
: Descriu l'estructura del document, les manipulacions i els esdeveniments, veure <https://dom.spec.whatwg.org>.

Especificació CSSOM
: Descriu els fulls i les regles d’estil, les manipulacions i la vinculació als documents d'aquests, veure <https://www.w3.org/TR/cssom-1/>.

Especificació HTML
: Descriu l’idioma HTML (per exemple, les etiquetes) i també el BOM (browser object model) -- diverses funcions del navegador: `setTimeout`, `alert`, `location` etcètera, veure <https://html.spec.whatwg.org>. Agafa l’especificació DOM i l’amplia amb moltes propietats i mètodes addicionals.

Ara aprendrem DOM, perquè el document té un paper vital en el UI.

Pots pendre nota dels enllaços anteriors, ja que hi ha tantes coses per aprendre que és impossible cobrir i recordar-ho tot.

Quan volguis llegir una propietat o un mètode, el manual de Mozilla a <https://developer.mozilla.org/en-US/search> és un bon recurs, però llegir les especificacions corresponents pot ser millor: és més complex i més llarg de llegir, però farà que el vostre coneixement fonamental sigui més complet.
