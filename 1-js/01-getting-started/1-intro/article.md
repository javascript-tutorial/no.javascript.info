# En introduksjon til JavaScript

Let's see what's so special about JavaScript, what we can achieve with it, and what other technologies play well with it.

La oss se litt nærmere på hva som er så spesielt med JavaScript, hva vi kan oppnå ved å bruke det, og hvilke andre teknologier som passer godt sammen med det.

<<<<<<< HEAD
## Hva er JavaScript?

*JavaScript* var egentlig ment for å *"gi hjemmesider mer liv"*.
=======
*JavaScript* was initially created to "make web pages alive".

The programs in this language are called *scripts*. They can be written right in a web page's HTML and run automatically as the page loads.
>>>>>>> 0599d07b3c13ee25f583fc091cead3c17a7e7779

Programmer skrevet i JavaScript kalles for *scripts*. De kan skrives rett inn i en nettsides's HTML og kjører automatisk så fort siden blir lastet.

Scripts er utdelt og kjørt som ren tekst. De trenger altså ingen forberedelser eller å bli kompilert for å kjøre.

Med dette øyemed, er JavaScript veldig annerledes fra et annet språk kalt [Java](https://en.wikipedia.org/wiki/Java_(programming_language)).

<<<<<<< HEAD
```smart header="Why <u>Java</u>Script?"
Når JavaScript ble skapt, hadde det i utgangspunktet navnet: "LiveScript". Men Java var veldig populært på den tiden, så det ble bestemt at å presentere et nytt programmeringsspråk som en "lillebror" til Java ville være en god ide.
=======
```smart header="Why is it called <u>Java</u>Script?"
When JavaScript was created, it initially had another name: "LiveScript". But Java was very popular at that time, so it was decided that positioning a new language as a "younger brother" of Java would help.
>>>>>>> 0599d07b3c13ee25f583fc091cead3c17a7e7779

Men etterhvert som det utviklet seg ble JavaScript et helt uavhengig programmeringsspårk med sitt eget sett med spesifikasjoner kalt [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript), og nå har det ingenting med Java å gjøre i det hele tatt.
```

Idag kan JavaScript kjøres på serveren, og ikke bare i nettleseren lenger, faktisk kan det kjøres på hvilken som helst enhet som har [the JavaScript engine](https://en.wikipedia.org/wiki/JavaScript_engine) installert.

Nettleseren har en innebygget motor som noenganger blir kalt for en "JavaScript virtuell maskin".

Different engines have different "codenames". For example:
Det finnes flere forskjellige motorer som har skilles fra hverandre med forskjellige "kodenavn". For eksempel:

<<<<<<< HEAD
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- i Chrome og Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- i Firefox.
- ...Det er også andre kodenavn som "Trident" og "Chakra" for forskjellige versjoner av IE, "ChakraCore" for Microsoft Edge, "Nitro" og "SquirrelFish" for Safari, osv.
=======
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- in Chrome and Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- in Firefox.
- ...There are other codenames like "Chakra" for IE, "ChakraCore" for Microsoft Edge, "Nitro" and "SquirrelFish" for Safari, etc.
>>>>>>> 0599d07b3c13ee25f583fc091cead3c17a7e7779

Begrepene ovenfor er gode å huske fordi de ofte brukt i artikler skrevet av utviklere på nettet. Vi vil bruke de også. For eksempel, hvis "en funksjon x er støttet av v8", vil den sannsynlig fungere i Chrome og Opera.

```smart header="How do engines work?"

Motorer er kompliserte. Men det grunnleggende er ganske lett.

1. Motoren (Innebygd hvis det er en nettleser) leser ("parser") scriptet.
2. Så konverterer den ("kompilerer") scriptet til maskin språk
3. Og så kjører maskin koden, veldig raskt.

<<<<<<< HEAD
Motoren tar ibruk optimaliseringer til hver eneste steg i prosessen. Passer til og med på det kompilerte scriptet imens det kjører, analyserer data som flyter gjennom det, og legger så til optimaliseringer til maskin koden basert på denne kunnskapen. 
Når dette gjøres, kjører scripts rimelig fort.
=======
The engine applies optimizations at each step of the process. It even watches the compiled script as it runs, analyzes the data that flows through it, and further optimizes the machine code based on that knowledge.
>>>>>>> 0599d07b3c13ee25f583fc091cead3c17a7e7779
```

## Hva kan JavaScript gjøre i nettleseren?

Moderne JavaScript er et "trygt" programmeringsspråk. Det gir ikke lavniå tilgang til minne eller CPU, fordi det i utgangspunktet var laget for nettlesere som ikke krever det.

JavaScript's evber er sterkt avhengig av miljøet det kjører i. For eksempel, [Node.js](https://wikipedia.org/wiki/Node.js) støtter funksjoner som lar JavaScript lese/skrive vilkårlig, gjennomføre nettverksforespørsler, osv.

I-nettleser JavaScript kan gjøre alt i forbindelse med manipulering av nettsider, interaksjon med brukeren, og nett-tjeneren.

For eksempel, i-nettleser JavaScript er i stand til å:

- Legge til ny HTML til en side, endre den eksisterende konteksten, modifisere stiling.
- Reagere på nye hendelser, kjøre ved museklikk, peker bevegelser, tastetrykk.
- Sende forespørsler over nettverket til eksterne tjenere, nedlasting og opplasting av filer (såkalte [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) og [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) teknologier).
- Kalle på og endre [informasjonskapsler](https://no.wikipedia.org/wiki/Informasjonskapsel), stille spørsmål til besøkende, vise meldinger.
- Huske data på klientsiden ("lokal lagring").

## Hva KAN IKKE JavaScript gjøre i nettleseren?

JavaScript's egenskaper i nettleseren er begrensede på vegne av brukeren trygghet. Dette er ment for å hindre nettsider med onde hensikter fra å aksessere informasjon eller ramme brukerens data på noen som helst måte.

Eksempler på slike begrensninger inkluderer:

- JavaScript på en nettside kan ikke lese/skrive vilkårlige filer på en harddisk, kopiere eller kjøre programmer. Det har ingen direkte tilgang til funksjoner som er tilknyttet operativsystemet (OS).

<<<<<<< HEAD
    Moderne nettlesere tillater det til å behandle filer, men denne adgangen er begrenset og kun gitt hvis brukeren gjennomfører utvalgte hendelser, som å "slippe" en fil over et nettleservindu eller velger det via en `<input>` tag.
=======
- JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs. It has no direct access to OS functions.
>>>>>>> 0599d07b3c13ee25f583fc091cead3c17a7e7779

    Det finnes måter å interragere med kamera og mikrofon og andre enheter, men disse krever at brukeren gir eksplisitt tillatelse. Så en JavaScript-akrivert side kan ikke på en lumsk måte aktivere webkameraet, se seg rundt og sende informasjonen om dette til [PST](https://no.wikipedia.org/wiki/Politiets_sikkerhetstjeneste).

<<<<<<< HEAD
- Forskjellige paneler/vinduer i en nettleser vet i utgangspunktet ingenting om hverandre. Noenganger gjør de det, for eksempel når et vindu bruker JavaScript til å åpne et annet vindu. Men selv i dette tilfellet, JavaScript fra en side til en kan ikke aksessere et annet vindu hvis det kommer fra forskjellige sider (fra et annet domene, protokoll eller port).

    Dette er kalt "Same Origin Policy". For å jobbe rundt dette, må *begge sidene* inneholde en spesiell JavaScript kode som behandler denne utvekslingen av data.
=======
    There are ways to interact with camera/microphone and other devices, but they require a user's explicit permission. So a JavaScript-enabled page may not sneakily enable a web-camera, observe the surroundings and send the information to the [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Different tabs/windows generally do not know about each other. Sometimes they do; for example when one window uses JavaScript to open the other one. But even in this case, JavaScript from one page may not access the other if they come from different sites (from a different domain, protocol or port).

    This is called the "Same Origin Policy". To work around that, *both pages* must agree for data exchange and contain a special JavaScript code that handles it. We'll cover that in the tutorial.
>>>>>>> 0599d07b3c13ee25f583fc091cead3c17a7e7779

    Denne begrensningen er, igjen satt på plass med brukerens trygghet i tankene. En side fra `http://hvilkensomhelstside.no` som en bruker har åpnet kan overhodet ikke være i stand til å aksessere et annet panel med URL'en `http://gmail.com` og stjele informasjon derfra.

<<<<<<< HEAD
- JavaScript kan med letthet kommunisere med en tjener over nettet hvor den nåværende siden kom fra. Men dets egenskap til å motta data fra andre sider/domener er veldig tungvint, men det er mulig, dette krever eksplisitt tillatelse (uttrykt via HTTP headere) fra den eksterne siden. Igjen, dette er sikkerhetsbegrensning.
=======
![](limitations.svg)
>>>>>>> 0599d07b3c13ee25f583fc091cead3c17a7e7779

![](limitations.svg)

Slike begrensninger eksisterer ikke hvis JavaScript brukes på utsiden av nettleseren, for eksempel på en tjener. Moderne nettlesere tillater også bruk utvidelser som kan spørre om utvidede tillatelser.

## Hva gjør JavaScript unikt?

Dette er de *tre* minst gode ting om JavaScript:

```compare
+ Full integrasjon med HTML/CSS.
+ Enkle ting kan gjøres på en enkel måte.
+ Støttet av alle de største nettleserne og er påslått som standard.
```
JavaScript er den eneste nettleser teknologien som kombinerer disse tre tingene.

<<<<<<< HEAD
Dette er det som gjør JavaScript unikt. Dette er grunnen til at JavaScript er det mest utstrakte verktøyet for utvikling av grensesnitt i nettleseren.

Imens du har planer om å lære deg en teknologi, er det gunstig å sjekke dens perspektiver. Så la oss fortsette til de moderne trendene som påvirker den, inkluderende nye språk og ny nettleser-funksjonalitet.
=======
That said, JavaScript also allows to create servers, mobile applications, etc.
>>>>>>> 0599d07b3c13ee25f583fc091cead3c17a7e7779

## Språk "via" JavaScript

JavaScript's syntax er tilpasset alle sitt behov. Forskjellige folk trenger forskjellige funksjoner.

Dette er ikke overraskende, siden forskjellige prosjekter har forskjellige krav.

En haug av nye språk har nylig dukket opp, som er *transpilert* (konvertert) til JavaScript før de kjører i nettleseren.

Moderne verktøy gjør transpileringen veldig rask og forutsigbar, faktisk så lar dette utviklere å skrive kode på et annet språk som blir automatisk konvertert "under panseret".

Dette er eksempler på slike språk:

<<<<<<< HEAD
- [CoffeeScript](http://coffeescript.org/) er en "syntaktisk sukker" for JavaScript. Det introduserer kortere syntax, som lar oss skrive klarer og mer presis kode. Ruby utviklere er vanligvis mer glad i dette.
- [TypeScript](http://www.typescriptlang.org/) er konsentrert rundt å legge til "streng datatyping" for å gjøre utvikling og drifting av komplekse systemer lettere. TypeScript er utviklet av Microsoft.
- [Dart](https://www.dartlang.org/) er et selvstendig språk som har sin egen motor som kjører ukjente miljøer for nettleseren (som mobilapplikasjoner). Det var i utgangspunktet lagt frem av Google som en erstatter for JavaScript, men foreløpig krever nettlesere at Dart transpileres til JavaScript akkurat som de andre nevnt ovenfor.

Det finnes flere selvfølgelig. Men selv om vi bruker noen av disse språkene, er det lurt av oss å kjenne JavaScript for å vite hva vi egentlig driver med.
=======
- [CoffeeScript](http://coffeescript.org/) is a "syntactic sugar" for JavaScript. It introduces shorter syntax, allowing us to write clearer and more precise code. Usually, Ruby devs like it.
- [TypeScript](http://www.typescriptlang.org/) is concentrated on adding "strict data typing" to simplify the development and support of complex systems. It is developed by Microsoft.
- [Flow](http://flow.org/) also adds data typing, but in a different way. Developed by Facebook.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript. Developed by Google.
- [Brython](https://brython.info/) is a Python transpiler to JavaScript that allow to write application in pure Python without JavaScript.

There are more. Of course, even if we use one of transpiled languages, we should also know JavaScript to really understand what we're doing.
>>>>>>> 0599d07b3c13ee25f583fc091cead3c17a7e7779

## Summary
## Oppsummering

<<<<<<< HEAD
- JavaScript var i utgangspunktet skapt som et kun-nettleser språk, men finnes også i mange andre miljøer i tillegg.
- Idag, har JavaScript en unik position som det mest brukt nettleser språket med full integrasjon mot HTML/CSS.
- Det finnes mange språk som blir "transpilert" til JavaScript og som gir utvalgte funksjoner. Det er anbefalt å ta en kikk på de, ihvertfall ganske kort, etter at du mestrer JavaScript.
=======
- JavaScript was initially created as a browser-only language, but it is now used in many other environments as well.
- Today, JavaScript has a unique position as the most widely-adopted browser language with full integration in HTML/CSS.
- There are many languages that get "transpiled" to JavaScript and provide certain features. It is recommended to take a look at them, at least briefly, after mastering JavaScript.
>>>>>>> 0599d07b3c13ee25f583fc091cead3c17a7e7779
