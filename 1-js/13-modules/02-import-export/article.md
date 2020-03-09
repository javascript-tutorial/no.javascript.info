# Export and Import

<<<<<<< HEAD
Export og import direktiver er veldig allsidige.
=======
Export and import directives have several syntax variants.
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

I forrige kapittel så vi en enklere bruk av disse, la oss nå utforske flere eksempler.

## Export før deklareringer

Vi kan merke enhver deklarasjon som eksportert ved å skrive `export` før det, så lenge det gjøres før deklarasjon av en variabel, funksjon eller en klasse.

For eksempel, alle disse er gyldig bruk av eksportering:

```js
// eksporter et array
*!*export*/!* let months = ['Jan', 'Feb', 'Mar','Apr', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];

// eksporter en konstant
*!*export*/!* const MODULES_BECAME_STANDARD_YEAR = 2015;

// eksporter en klasse
*!*export*/!* class User {
  constructor(name) {
    this.name = name;
  }
}
```

````smart header="No semicolons after export class/function"
<<<<<<< HEAD
Vennligst legg merke til at `export` før en klasse, eller en funksjon vil ikke gjøre den til et [funksjons utrykk](info:function-expressions-arrows). Det er fremdeles en deklarasjon av en funksjon, bare eksportert.

De fleste JavaScript stilguidene anbefaler bruk av semikolon etter utrykk, men ikke etter deklarering av funskjoner og klasser.

That's why there should be no semicolons at the end of `export class` and `export function`.
Dette er fordi det aldri skal være semikolon etter slutten av `export class` og `export function`.
=======
Please note that `export` before a class or a function does not make it a [function expression](info:function-expressions). It's still a function declaration, albeit exported.

Most JavaScript style guides don't recommend semicolons after function and class declarations.

That's why there's no need for a semicolon at the end of `export class` and `export function`:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
export function seyHi(user) {
  alert(`Hi, ${user}!`);
} *!* // no ; at the end */!*
```

````

## Export fraskilt fra deklarasjon

Vi kan også sette `export` separat fra et utrykk.

Først deklarerer vi, også eksporterer vi:

```js  
// 📁 say.js
export function sayHi(user) {
  alert(`Hi, ${user}!`);
}

function sayGoodbye(user) {
  alert(`Goodbye, ${user}!`);
}

*!*
export {sayHi, sayGoodbye}; // en liste av eksporterte variabler
*/!*
```

... eller, teksnisk sett kan vi sette `export` over funksjoner også.

## Import *

<<<<<<< HEAD
Vanligvis, kan vi putte en liste av hva som skal importeres inni `import {...}`, slik som dette:
=======
Usually, we put a list of what to import in curly braces `import {...}`, like this:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
// 📁 main.js
*!*
import {sayHi, sayGoodbye} from './say.js';
*/!*
sayHi('John'); // Hi, John!
sayGoodbye('John'); // Goodbye, John!
```

<<<<<<< HEAD
Men hvis denne listen er lang, kan vi importere alt som et objekt ved å bruke `import * as <obj>`, for eksempel:
=======
But if there's a lot to import, we can import everything as an object using `import * as <obj>`, for instance:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
// 📁 main.js
*!*
import * as say from './say.js';
*/!*

say.sayHi('John');
say.sayGoodbye('John');
```

Ved første øyekast, "importer alt" virker som en kul ting å gjøre, kort å skrive, hvorfor skulle vi noensinne eksplisitt liste opp hva vi trenger og importere?

Vel, det er noen få grunner.

1. Moderne byggverktøy ([webpack](http://webpack.github.io) og andre) pakker moduler sammen og optimaliserer de til å kunne raske laste og fjeren unyttige ting.

<<<<<<< HEAD
    La oss si, at vi la til et 3. partibibliotek `lib.js` inn i prosjektet med mange funksjoner:
=======
    Let's say, we added a 3rd-party library `say.js` to our project with many functions:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a
    ```js
    // 📁 say.js
    export function sayHi() { ... }
    export function sayGoodbye() { ... }
    export function becomeSilent() { ... }
    ```

<<<<<<< HEAD
    Nå hvis vi kun trenger en av disse in prosjektet vårt:
=======
    Now if we only use one of `say.js` functions in our project:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a
    ```js
    // 📁 main.js
    import {sayHi} from './say.js';
    ```
<<<<<<< HEAD
    ... Da vil optimalisereren automatisk oppdate det og helt fjerne de andre funksjonene fra den sammenpakkede koden, som vil gjøre det ferdige bygget mindre. Dette er kalt "treristing".

2. Eksplisit listing av hva som skal importeres gir kortere navn: `siHei()` istedenfor `lib.siHei()`.
3. Eksplisite importeringer gir en bedre oversikt av kodestrukturen; hva som blir brukt og hvor det blir brukt. Dette gjør vedlikehold og refaktorering av koden lettere.

## Import "as"

Vi kan også bruke `as` til å importere under forskjellige alias.
For eksempel, la oss importere `siHei` inn i den lokale variabelen `hei` for korthet i koden, og det samme for `siFarvel`:
=======
    ...Then the optimizer will see that and remove the other functions from the bundled code, thus making the build smaller. That is called "tree-shaking".

2. Explicitly listing what to import gives shorter names: `sayHi()` instead of `say.sayHi()`.
3. Explicit list of imports gives better overview of the code structure: what is used and where. It makes code support and refactoring easier.

## Import "as"

We can also use `as` to import under different names.

For instance, let's import `sayHi` into the local variable `hi` for brevity, and import `sayBye` as `bye`:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
// 📁 main.js
*!*
import {sayHi as hi, sayGoodbye as goodbye} from './say.js';
*/!*

hi('John'); // Hi, John!
goodbye('John'); // goodbye, John!
```

## Export "as"

Lignende syntaks eksisterer også for `export`.

La oss eksportere funksjoner som `hei` og `farvel`:

```js
// 📁 say.js
...
export {sayHi as hi, sayGoodbye as goodbye};
```

<<<<<<< HEAD
Nå er `hi` og `goodbye` offisielle navn for parter utenfor:
=======
Now `hi` and `bye` are official names for outsiders, to be used in imports:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
// 📁 main.js
import * as say from './say.js';

<<<<<<< HEAD
say.hi('John'); // Hi, John!
say.goodbye('John'); // Goodbye, John!
=======
say.*!*hi*/!*('John'); // Hello, John!
say.*!*bye*/!*('John'); // Bye, John!
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a
```

## Export default

<<<<<<< HEAD
Så langt har vi sett på hvordan man importerer/eksporterer flere ting, valgfritt som (`as`) andre navn.

I praksis, modulere inneholder enten:
- Et bibliotek, samling av funksjoner, som `lib.js`.
- Eller et objekt som `class User` er beskrevet i `user.js`, hele modulen har kun denne klassen.
=======
In practice, there are mainly two kinds of modules.

1. Modules that contain a library, pack of functions, like `say.js` above.
2. Modules that declare a single entity, e.g. a module `user.js` exports only `class User`.
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

Som oftest, er den andre måten å ta ibruk foretrukket, sånn at hver "ting" oppholdes i sin egen modul.

<<<<<<< HEAD
Naturligvis, dette krever en hel del filer, som alle vil ha sin egen modul, men dette er ikke et problem. Faktisk, så blir navigering av kodebasen lettere, hvis filene er gitt bra navn og strukturert godt i egne mapper.

Moduler gir spesielle `export default` syntaks for å gjøre at "en ting per modul" ser bedre ut.

Det krever følgende `export` og `import` uttrykk:

1. Legg `export default` før "hoved eksporten" i modulen.
2. Kall `import` uten krøllparenteser.

For eksempel, her `bruker.js` exports `class Bruker`:
=======
Naturally, that requires a lot of files, as everything wants its own module, but that's not a problem at all. Actually, code navigation becomes easier if files are well-named and structured into folders.

Modules provide special `export default` ("the default export") syntax to make the "one thing per module" way look better.

Put `export default` before the entity to export:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
// 📁 user.js
export *!*default*/!* class User { // kun tilføy "default"
  constructor(name) {
    this.name = name;
  }
}
```

<<<<<<< HEAD
...Og `main.js` importerer det:
=======
There may be only one `export default` per file.

...And then import it without curly braces:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
// 📁 main.js
import *!*User*/!* from './user.js'; // ikke {User}, kun User
new User('John');
```

<<<<<<< HEAD
Importsetninger uten krøllparentes ser finere ut. En vanlig feil når man begynner å bruke moduler er å glemme krøllparentes helt. Så, husk, `import` trenger krøllparentes for navngitte importsetninger og trenger dem ikke ikke default import.
=======
Imports without curly braces look nicer. A common mistake when starting to use modules is to forget curly braces at all. So, remember, `import` needs curly braces for named exports and doesn't need them for the default one.
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

| Navngitt export | Default export |
|--------------|----------------|
| `export class User {...}` | `export default class User {...}` |
| `import { User } from ...` | `import User from ...`|

<<<<<<< HEAD
Naturligvis kan det kun være en "default" export per fil.

Vi kan ha både default og navngitt eksporteringer i en enkelt modul, men i praksis vil folk blande disse to. En modul har enten navngitte eksporteringer eller en default.

**En annen ting å bite seg merke i er at navngitt eksporteringer må (naturligvis) ha et navn, mens `export default` kan være anonym.**
=======
Technically, we may have both default and named exports in a single module, but in practice people usually don't mix them. A module has either named exports or the default one.

As there may be at most one default export per file, the exported entity may have no name.
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

For eksempel, disse er alle helt gyldige eksporteringer:

```js
export default class { // ingen klassenavn
  constructor() { ... }
}
```

<<<<<<< HEAD
export default function(user) { // ingen funksjonsnavn
  alert(`Hi, ${user}!`);
=======
```js
export default function(user) { // no function name
  alert(`Hello, ${user}!`);
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a
}
```

<<<<<<< HEAD
// eksporter en enkelt verdi, uten å definere en variabel
export default ['Jan', 'Feb', 'Mar','Apr', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
```

Det går helt fint, fordi `export default` finnes det kun en av per fil, så `import` vet alltid hva som skal importeres.
 I motsetning til det, og utelater et navn for navngitte importeringer ville vært en feil i koden:
=======
```js
// export a single value, without making a variable
export default ['Jan', 'Feb', 'Mar','Apr', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
```

Not giving a name is fine, because `export default` is only one per file, so `import` without curly braces knows what to import.

Without `default`, such export would give an error:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
export class { // Feil! (ikke-default eksportering trenger et navn)
  constructor() {}
}
```

### The "default" name

<<<<<<< HEAD
Stikkordet "default" er et slags alias for default export, for når vi trenger å angi en referanse for den. 

For example, if we already have a function declared, that's how to `export default` it:
For eksempel, når vi allerede har deklarert en funksjon, er dette hvordan `export default` den:
=======
In some situations the `default` keyword is used to reference the default export.

For example, to export a function separately from its definition:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
function sayHi(user) {
  alert(`Hi, ${user}!`);
}

<<<<<<< HEAD
export {sayHi as default}; // samme som hvis vi hadde lagt til "export default" før funksjonen
```

Eller, la oss si at modulen `user.js` eksporterer en hoved "default" ting og et par navngitte noen (sjeldent tilfelle, men skjer av og til):
=======
// same as if we added "export default" before the function
export {sayHi as default};
```

Or, another situation, let's say a module `user.js` exports one main "default" thing and a few named ones (rarely the case, but happens):
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
// 📁 user.js
export default class User {
  constructor(name) {
    this.name = name;
  }
}

export function sayHi(user) {
  alert(`Hi, ${user}!`);
}
```

Dette er hvordan vi importer default export sammen med navngitte exports:

```js
// 📁 main.js
import { *!*defualt as User*/!*, sayHi } from './user.js';

new User('John');
```

<<<<<<< HEAD
Eller hvis vi vurderer å importere `*` som et objekt, da må `default` egenskapen være eksagt default export:
=======
And, finally, if importing everything `*` as an object, then the `default` property is exactly the default export:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
// 📁 main.js
import * as User from './user.js';

let User = user.default; // the default export
new User('John');
```

<<<<<<< HEAD
### Burde jeg bruker default exports?

Vi må være forsiktige når vi bruker default exports, fordi disse kan være til en viss grad veldig annerledes å vedlikeholde.
=======
### A word against default exports
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

Navngitte exports er eksplisitte. De navngir eksagt hva de importerer, slik at vi har den informasjonen når vi importerer de, Det er en bra ting.

<<<<<<< HEAD
I tillegg, navngitte exports tvinger oss til ta ibruk deres eksagte navn for å ta de ibruk:

```js
import { User } from './user.js';
```

For default exports, trenger vi å lage et navn på egenhånd:

```js
import MyUser from './user.js'; // dette kunne vært importer hvasomhelst... , og det ville fungert helt fint
```

Slik at det blir så lite frihet som mulig til at dette kan brukes feil, slik at team medlemmer kan bruke forskjellige navn for den samme tingen.
Vanligvis, for å unngå dette og holde koden mer konsistent, er det regel for at importerte variabler burde stemmer overens med sitt filnavn, f.eks:
=======
Named exports enforce us to use exactly the right name to import:

```js
import {User} from './user.js';
// import {MyUser} won't work, the name must be {User}
```

...While for a default export, we always choose the name when importing:

```js
import User from './user.js'; // works
import MyUser from './user.js'; // works too
// could be import Anything... and it'll still work
```

So team members may use different names to import the same thing, and that's not good.

Usually, to avoid that and keep the code consistent, there's a rule that imported variables should correspond to file names, e.g:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
import User from './user.js';
import LoginForm from './loginForm.js';
import func from '/path/to/func.js';
...
```

<<<<<<< HEAD
En annen løsning ville vært å bruke navngitte exports overalt. Til og med hvis kun en enkelt fil er eksportert, er den fremdeles eksportert under et navn, uten `default`.
=======
Still, some teams consider it a serious drawback of default exports. So they prefer to always use named exports. Even if only a single thing is exported, it's still exported under a name, without `default`.
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

Dette gjør også re-export (se under) litt enklere å forstå.

## Re-export

"Re-export" syntaks `export ... from ...` lar ss importere ting og med en eksportere de (også mulig under andre navn enn importert), slik:


```js
<<<<<<< HEAD
export { sayHi } from './say.js';
export { default as User } from './user.js';
```

Hva er poenget, hvorfor trenger vi dette? La oss se på et praktisk bruksområde.

Se for deg, vi skriver en "pakke": en mappe med mange moduler, mest til bruk internt, med noe funksjonalitet eksportert utad (verktøy som NPM lar oss publisere og distribuere pakker, men det har ikke noe å si her).

En mappestruktur kan være slik:
=======
export {sayHi} from './say.js'; // re-export sayHi

export {default as User} from './user.js'; // re-export default
```

Why would that be needed? Let's see a practical use case.

Imagine, we're writing a "package": a folder with a lot of modules, with some of the functionality exported outside (tools like NPM allow to publish and distribute such packages), and many modules are just "helpers", for the internal use in other package modules.

The file structure could be like this:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a
```
auth/
    index.js  
    user.js
    helpers.js
    tests/
        login.js
    providers/
        github.js
        facebook.js
        ...
```

Vi vil eksponere pakkens funksjonalitet via et enkelt entry point, "hovedfilen" `auth/inde.js`, kan være slik:

```js
import {login, logout} from 'auth/index.js'
```

<<<<<<< HEAD
Ideen er at parter fra utsiden, utviklere som bruker pakken vår, ikke bør tenke på dens interne struktur. De skal ikke måtte lete etter filer inne i vår pakke. Vi eksportert kun det som er nødvendig gjennom `auth/inde.js` og holder resten skjult fra nysgjerrige øyne

Nå som den faktiske eksporterte funksjonaliteten er spredt blant pakken, kan vi samle og "re-export" den i `auth/index.js`:
=======
The idea is that outsiders, developers who use our package, should not meddle with its internal structure, search for files inside our package folder. We export only what's necessary in `auth/index.js` and keep the rest hidden from prying eyes.

As the actual exported functionality is scattered among the package, we can import it into `auth/index.js` and export from it:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
// 📁 auth/index.js

// import login/logout and immediately export them
import {login, logout} from './helpers.js';
export {login, logout};

// import default as User and export it
import User from './user.js';
export {User};
...
```

<<<<<<< HEAD
"Re-eksportering" er bare en måte å gjøre slik på:
=======
Now users of our package can `import {login} from "auth/index.js"`.

The syntax `export ... from ...` is just a shorter notation for such import-export:
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

```js
// 📁 auth/index.js
// import login/logout and immediately export them
export {login, logout} from './helpers.js';

// import default as User and export it
export {default as User} from './user.js';
...
```

<<<<<<< HEAD
````warn header="Re-eksporering default kan være vrient" 
Vær grei å merk: `export User from './user.js'` vill ikke virke. Dette er faktisk en syntaks feil. For å re-export en default export, må vi referensere den eksplisitt slik som `{default as ...}`, slik som eksempelet over.

I tillegg, er det en annen særhet: `export * from './user.js'` re-exports er kun navngitte eksporteringer, ekskludert standard eksport. Men igjen, vi må nevne den eksplisitt.

For eksempel, for å re-export alt, trenger vi to uttrykk:
=======
### Re-exporting the default export

The default export needs separate handling when re-exporting.

Let's say we have `user.js`, and we'd like to re-export class `User` from it:

>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a
```js
// 📁 user.js
export default class User {
  // ...
}
```

<<<<<<< HEAD
Standarden burde være nevnt eksplisitt kun når man re-eksporterer: `import * as obj` virker fint. Dette importerer en standard export som `obj.default`. Slik at det er en liten asymmetry mellom import og export konstruksjoner her.
````
=======
1. `export User from './user.js'` won't work. What can go wrong?... But that's a syntax error!

    To re-export the default export, we have to write `export {default as User}`, as in the example above.    

2. `export * from './user.js'` re-exports only named exports, but ignores the default one.

    If we'd like to re-export both named and the default export, then two statements are needed:
    ```js
    export * from './user.js'; // to re-export named exports
    export {default} from './user.js'; // to re-export the default export
    ```

Such oddities of re-exporting the default export are one of the reasons why some developers don't like them.
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

## Sammendrag

<<<<<<< HEAD
Det er følgende typer av `export`:

- Før deklarering:
  - `export [default] class/function/variable ...`
- Enkeltvis:
  - `export {x [as y], ...}`.
- Re-export:
  - `export {x [as y], ...} from "mod"`
  - `export * from "mod"` (vil ikke re-export standard).
  - `export {default [as y]} from "mod"` (re-export standard).

Import:

- Navngitte exports fra modul:
  - `import {x [as y], ...} from "mod"` 
- Standard export:
  - `import x from "mod"`
  - `import {default as x} from "mod"`
- Alt fra "mod" modul:
  - `import * as obj from "mod"`
- Kun hent/evaluer modulen, ikke importer:
  - `import "mod"`
=======
Here are all types of `export` that we covered in this and previous chapters.

You can check yourself by reading them and recalling what they mean:

- Before declaration of a class/function/..:
  - `export [default] class/function/variable ...`
- Standalone export:
  - `export {x [as y], ...}`.
- Re-export:
  - `export {x [as y], ...} from "module"`
  - `export * from "module"` (doesn't re-export default).
  - `export {default [as y]} from "module"` (re-export default).

Import:

- Named exports from module:
  - `import {x [as y], ...} from "module"`
- Default export:  
  - `import x from "module"`
  - `import {default as x} from "module"`
- Everything:
  - `import * as obj from "module"`
- Import the module (its code runs), but do not assign it to a variable:
  - `import "module"`
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

We can put `import/export` statements at the top or at the bottom of a script, that doesn't matter.

<<<<<<< HEAD
Så dette er teknisk rett:
```js
sayHi();

import {sayHi} from './say.js'; // import på slutten av filen
```

I praksis så er imports vanligvis deklarert i begynnelsen av hver enkelt filt, men det er kun av praktiske årsaker.
=======
So, technically this code is fine:
```js
sayHi();

// ...

import {sayHi} from './say.js'; // import at the end of the file
```

In practice imports are usually at the start of the file, but that's only for more convenience.
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

**Vær grei å legg merke til at import/export uttrykk ikke vil hvis de er plasser inne i `{...}`.**

Betinget import, som dette vil ikke fungere:
```js
if (something) {
  import {sayHi} from "./say.js"; // Feil: import må være på øverste nivå i modulen.
}
```

...Men hva hvis vi virkelig trenger å  importere noe basert på en betingelse? Eller på riktig tidspunkt i koden? Slik som, laste inn en modul på forespørsel, når den virkelig trengs?

Vi skal se på dynamiske import i neste kapittel.
