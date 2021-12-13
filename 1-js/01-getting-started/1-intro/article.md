# Uvod v JavaScript

Poglejmo si kaj je tako posebnega z JavaScript-om, kaj vse lahko z njim dosežemo
ter katere tehnologije delujejo dobro uparjene z JavaScript.

## Kaj je JavaScript?

_JavaScript_ je bil prvotno ustvarjen da "oživi spletne strani".

Programi v tem programskem jeziku se imenujejo _skripte_. Te lahko spišemo
direktno v HTML-ju spletne strani in jih tako avtomatično poženemo ob nalaganju
strani.

Skripte se napišejo ter se izvršijo v čisti tekstovni obliki. Ni potreben noben
specialen prevajalnik ali kakšna posebna priprava. Na primer spletni brskalniki
imajo vgrajen program (angl. _engine_), ki izvede prevajanje tekstovne oblike
kode v strojno ob izvedbi programa. Takšne prevajalnike imenujemo _Just-In-Time_
ali _Run-Time_ prevajalniki.

V tem kontekstu je JavaScript precej drugačen od programskega jezika, ki ga
poznamo pod imenom
[Java](<https://en.wikipedia.org/wiki/Java_(programming_language)>).

```smart header="Zakaj se imenuje prav <u>Java</u>Script?"
Prvotno poimenovanje za JavaScript je bilo "LiveScript". Ampak ker je v tistem času bila Java tako popularen programski jezik so se ustvarjalci JavaScript-a odločili postaviti novi programski jezik kot "mlajši brat" Java-e.
S tem so menili, da bo to pomagalo pri prepoznavnosti tega jezika.

Z razvojem je JavaScript postal povsem samostojen in neodvisen programski jezik, ki ima tudi svojo ustrezno specifikacijo, ki se imenuje [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript).
Tako več nima nobene povezave z Java-o.
```

Danes lahko JavaScript izvedemo ne le v spletnem brskalniku, ampak tudi na
strežnikih oziroma pravzaprav na katerikoli napravi, ki uporablja
[JavaScript engine](https://en.wikipedia.org/wiki/JavaScript_engine).

Spletni brskalniki uporabljajo različna imena za JavaScript engine:

- [V8](<https://en.wikipedia.org/wiki/V8_(JavaScript_engine)>) -- Chrome in
  Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- Firefox.
- [Chakra](<https://en.wikipedia.org/wiki/Chakra_(JavaScript_engine)>) -- IE.
- [WebKit](<https://en.wikipedia.org/wiki/Safari_(web_browser)>) -- Safari
- ...Obstajajo še druga imena kot je "ChakraCore" za Microsoft Edge ipd.

<<<<<<< HEAD
Zgornja poimenovanja si velja zapomniti saj se velikokrat pojavijo v raznih
člankih razvijalcev, kjer jih navadno omenjajo kadar govorijo o podpori določene
funkcionalnosti. Na primer: "lastnost X je podprta na V8", kar pomeni, da to
lastnost lahko uporabimo na brskalnikih Chrome in Opera.

```smart header="Kako delujejo programski stroji (angl. *engines*)?"
=======
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- in Chrome, Opera and Edge.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- in Firefox.
- ...There are other codenames like "Chakra" for IE, "JavaScriptCore", "Nitro" and "SquirrelFish" for Safari, etc.

The terms above are good to remember because they are used in developer articles on the internet. We'll use them too. For instance, if "a feature X is supported by V8", then it probably works in Chrome, Opera and Edge.
>>>>>>> c5358c59494b53efb832c81a5338e0a23b22c269

Programski stroji so precej zahtevni za razumevanje. A osnove so enostavne.

1. Programski stroj prebere (angl.*parses*) skripto (v JavaScript je programski stroj največkrat kar vgrajen v spletni brskalnik, če se izvaja v spletni aplikaciji).
2. Nato jo prevede (angl. *compiles*) v strojni jezik.
3. Sledi izvedbe strojne kode, ki deluje zelo hitro.

Programski stroji opravijo dodatne optimizacije ob vsakem koraku v danem procesu. Pravtako imajo možnost opazovanja in analiziranje prevedene skripte, ki se poganja, in s tem dodatno optimizira strojno kodo glede na najdbe.
```

<<<<<<< HEAD
## Kaj lahko stori JavaScript, ki se izvede v spletnem brskalniku?

Sodobni JavaScript je "varen" programski jezik. To pomeni, da ne ponuja možnosti
dostopa do nizko-nivojskih funkcij spomina ali CPE, saj je bil inicialno
ustvarjen za spletne brskalnike, ki pa tega ne potrebujejo.

Sposobnosti JavaScript-a so močno odvisne od okolja v katerem se poganja. Na
primer [Node.js](https://wikipedia.org/wiki/Node.js) podpira funkcije, ki
dovolijo JavaScript-u, da bere/piše poljubne datoteke, opravlja omrežne zahteve
ipd.

JavaScript, ki se izvaja v spletnem brasklaniku lahko počne vse kar je v
povezavi z manipulacijo spletne strani, interakcijo z uporabniki ali spletnim
strežnikom. JavaScript (ki se izvede v spletnem brskalniku) lahko na primer:

- Doda nov HTML na stran, spremeni obstoječo vsebino, spremeni oblikovanja.
- Se odziva na uporabniške akcije, se poganja glede na klike z miško,
  premikanjem kazalnika, pritiskanjem tipk.
- Pošilja zahtevke preko omrežja do oddaljenih strežnikov, nalaga in prenaša
  datoteke (t.i. [AJAX](<https://en.wikipedia.org/wiki/Ajax_(programming)>) in
  [COMET](<https://en.wikipedia.org/wiki/Comet_(programming)>) technologies).
- Bere in nastavlja spletne piškotke, postavlja vprašanja obiskovalcem strani,
  prikazuje različna sporočila.
- Si zapomni (shrani) podatke na klientu ("local storage")

## Kaj JavaScript, ki se izvede v spletnem brskalniku, NE MORE počet?

Omejitve JavaScript-a, ki se izvaja v spletnem brskalniku so predvsem zaradi
varnosti uporabnika. Cilj je preprečiti zlonamernim spletnim stranem dostop do
ali neželjeno manipulacijo zasebnih podatkov uporabnika.

Primeri takih omejitev vključujejo:

- JavaScript na spletni strani ne more brati/pisati/kopirati ali izvajati
  poljubnih datotek na trdem disku. Nima neposrednega dostopa do funkcij
  operacijskega sistema.
- Različni zavihki/okna se ne zavedajo drug drugega. Takšen princip se imenuje
  "Same Origin Policy". Če želimo izmenjavati podatke med omenjenimi entitetami
  se morata _obe strani_ strinjati za izmenjavo podatkov ter uporabiti posebno
  JavaScript kodo, ki to izvede (več o tem kasneje v vodniku). V praksi ta
  omejitev pomeni, da spletna stran `http://anysite.com` ne more dostopati do
  podatkov iz zavihka `http://gmail.com` ter posledično ukrasti podatke od tam.
- Čeprav JavaScript lahko brez težav komunicira s strežnikom, ki je naložil
  spletno stran, ne more pa prejemati podatkov od drugih strežnikov. To lahko
  stori le, če obstaja ekspliciten dogovor (navadno izražen v HTTP glavi) z
  oddaljeno stranjo.

Izjeme:

- Sodobni brskalniki do določene mere dovolijo delo z datotekami, vendar dostop
  je omejen ter omogoče le če uporabnik naredi določeno akcijo kot je npr.:
  nalaganje datoteke v brskalnik preko "drop" funkcionalnosti ali pa preko
  izbire z `<input>` oznako.
- Obstajajo načini kako vzpostavit interakcijo s kamero ali mikrofonom ali
  drugih naprav, vendar te zahtevajo uporabnikovo posebno dovoljenje. To pomeni
  da JavaScript ne more na skrivno prisluškovat ali omogočit spletno kamero ter
  podatke pošiljati
  [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
=======
## What can in-browser JavaScript do?

Modern JavaScript is a "safe" programming language. It does not provide low-level access to memory or CPU, because it was initially created for browsers which do not require it.

JavaScript's capabilities greatly depend on the environment it's running in. For instance, [Node.js](https://wikipedia.org/wiki/Node.js) supports functions that allow JavaScript to read/write arbitrary files, perform network requests, etc.

In-browser JavaScript can do everything related to webpage manipulation, interaction with the user, and the webserver.

For instance, in-browser JavaScript is able to:

- Add new HTML to the page, change the existing content, modify styles.
- React to user actions, run on mouse clicks, pointer movements, key presses.
- Send requests over the network to remote servers, download and upload files (so-called [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) and [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) technologies).
- Get and set cookies, ask questions to the visitor, show messages.
- Remember the data on the client-side ("local storage").

## What CAN'T in-browser JavaScript do?

JavaScript's abilities in the browser are limited for the sake of a user's safety. The aim is to prevent an evil webpage from accessing private information or harming the user's data.

Examples of such restrictions include:

- JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs. It has no direct access to OS functions.

    Modern browsers allow it to work with files, but the access is limited and only provided if the user does certain actions, like "dropping" a file into a browser window or selecting it via an `<input>` tag.

    There are ways to interact with camera/microphone and other devices, but they require a user's explicit permission. So a JavaScript-enabled page may not sneakily enable a web-camera, observe the surroundings and send the information to the [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Different tabs/windows generally do not know about each other. Sometimes they do, for example when one window uses JavaScript to open the other one. But even in this case, JavaScript from one page may not access the other if they come from different sites (from a different domain, protocol or port).

    This is called the "Same Origin Policy". To work around that, *both pages* must agree for data exchange and contain a special JavaScript code that handles it. We'll cover that in the tutorial.

    This limitation is, again, for the user's safety. A page from `http://anysite.com` which a user has opened must not be able to access another browser tab with the URL `http://gmail.com` and steal information from there.
- JavaScript can easily communicate over the net to the server where the current page came from. But its ability to receive data from other sites/domains is crippled. Though possible, it requires explicit agreement (expressed in HTTP headers) from the remote side. Once again, that's a safety limitation.
>>>>>>> c5358c59494b53efb832c81a5338e0a23b22c269

![](limitations.svg)

Takšne omejitve ne obstajajo, če se JavaScript požene izven brskalnika (na
primer na strežniku). Sodobni brskalniki pravtako omogočajo vtičnike, ki lahko
zahtevajo za dodatna dovoljenja.

## Kaj je unikatnega pri JavaScript-u?

Obstajajo vsaj _tri_ odlične stvari o JavaScript-u:

```compare
<<<<<<< HEAD
+ Popolna integracija s HTML in CSS.
+ Enostavne stvari so izvedene preprosto.
+ Podpora v vseh glavnih brskalnikih, kjer je tudi samodejno omogočen.
=======
+ Full integration with HTML/CSS.
+ Simple things are done simply.
+ Supported by all major browsers and enabled by default.
>>>>>>> c5358c59494b53efb832c81a5338e0a23b22c269
```

<<<<<<< HEAD
JavaScript je edina tehnologija v brskalnikih ki omogoča vse troje hkrati in to
naredi JavaScript unikatnega. Zaradi tega je najbolj uporabljeno orodje za
ustvarjanje brskalniških vmesnikov.

Z JavaScript lahko pravtako razvijamo spletne strežnike, mobilne aplikacije,
itd.

## Programski jeziki, katerih se prevedejo v JavaScript

Sintaksa ki jo uporablja JavaScript morda ni primerna za vse. Različni ljudje si
želijo različne sposobnosti. To je tudi pričakovati saj projektne zahteve so
različne za vsakogar.

Tako se je nedavno razvilo ogromno število novih programskih jezikov, ki se na
koncu prevedejo v JavaScript, preden se izvedejov spletnem brskalniku.

Sodobna orodja omogočajo zelo hitro in transparentno prevajanje, kar omogoča
razvijalcem programiranje v drugem programskem jeziku, vmes pa se le-ta
avtomatično prevaja v JavaScript.

Nekaj primerov takšnih programskih jezikov:

- [CoffeeScript](http://coffeescript.org/) je t.i. "syntactic sugar" za
  JavaScript. Omogoča krajšo sintakso, kar nam omogoča pisanje bolj jasne in
  natančne kode. Navadno ga uporabljajo Ruby razvijalci.
- [TypeScript](http://www.typescriptlang.org/) se osredotoča na dodajanje
  striktosti pri tipih podatkov za olajšano vzdrževanje bolj kompleksnih
  sistemov. Razvija ga Microsoft.
- [Flow](http://flow.org/) pravtako dodaja tipiziranje, vendar na drugacen
  način. Razvija ga Facebook.
- [Dart](https://www.dartlang.org/) je povsem samostojen programski jezik, ki
  ima svoj programski stroj, ki se izvaja izven brskalniških okolij (kot so
  mobilne aplikacije), a se vseeno lahko prevede v JavaScript. Razvija ga
  Google.
- [Brython](https://brython.info/) je Pythonov prevajalnik za JavaScript, ki
  omogoča razvijanje aplikacij v Python-u.
- [Kotlin](https://kotlinlang.org/docs/reference/js-overview.html) je sodoben,
  jedrnat in varen programski jezik, ki se lahko tudi uporablja za razvoj
  spletnih aplikacij ali strežnikov.

Obstaja jih še več. Kljub temu, da obstaja več prevedenih programskih jezikov za
JavaScript, je le-ta tisti, ki se na koncu izvede torej je potrebno dobro znanje
samega JavaScript-a za dosledno razumevanje naših aplikacij.

## Povzetek

- Prvotno je bil JavaScript zasnovan kot programski jezik le za brskalnike, a je
  sedaj uporabljen tudi v drugih okoljih.
- Danes ima JavaScript unikatno mesto kot najbolj priznan brskalniški jezik s
  popolno integracijo z HTML in CSS.
- Obstaja veliko programskih jezikov ki se prevedejo v JavaScript in ponujajo
  določene funkcionalnosti. Po spoznavanju JavaScript-a ja zaželjeno, da se
  spoznamo tudi s kakšnim izmed njih.
=======
- JavaScript was initially created as a browser-only language, but it is now used in many other environments as well.
- Today, JavaScript has a unique position as the most widely-adopted browser language, fully integrated with HTML/CSS.
- There are many languages that get "transpiled" to JavaScript and provide certain features. It is recommended to take a look at them, at least briefly, after mastering JavaScript.
>>>>>>> c5358c59494b53efb832c81a5338e0a23b22c269
