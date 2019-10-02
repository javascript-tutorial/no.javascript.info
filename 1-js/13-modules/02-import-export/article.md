
# Export and Import

Export og import direktiver er veldig allsidige.

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
Vennligst legg merke til at `export` før en klasse, eller en funksjon vil ikke gjøre den til et [funksjons utrykk](info:function-expressions-arrows). Det er fremdeles en deklarasjon av en funksjon, bare eksportert.

De fleste JavaScript stilguidene anbefaler bruk av semikolon etter utrykk, men ikke etter deklarering av funskjoner og klasser.

That's why there should be no semicolons at the end of `export class` and `export function`.
Dette er fordi det aldri skal være semikolon etter slutten av `export class` og `export function`.

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

Vanligvis, kan vi putte en liste av hva som skal importeres inni `import {...}`, slik som dette:

```js
// 📁 main.js
*!*
import {sayHi, sayGoodbye} from './say.js';
*/!*
sayHi('John'); // Hi, John!
sayGoodbye('John'); // Goodbye, John!
```

Men hvis denne listen er lang, kan vi importere alt som et objekt ved å bruke `import * as <obj>`, for eksempel:

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

    La oss si, at vi la til et 3. partibibliotek `lib.js` inn i prosjektet med mange funksjoner:
    ```js
    // 📁 lib.js
    export function sayHi() { ... }
    export function sayGoodbye() { ... }
    export function becomeSilent() { ... }
    ```

    Nå hvis vi kun trenger en av disse in prosjektet vårt:
    ```js
    // 📁 main.js
    import {sayHi} from './lib.js';
    ```
    ... Da vil optimalisereren automatisk oppdate det og helt fjerne de andre funksjonene fra den sammenpakkede koden, som vil gjøre det ferdige bygget mindre. Dette er kalt "treristing".

2. Eksplisit listing av hva som skal importeres gir kortere navn: `siHei()` istedenfor `lib.siHei()`.
3. Eksplisite importeringer gir en bedre oversikt av kodestrukturen; hva som blir brukt og hvor det blir brukt. Dette gjør vedlikehold og refaktorering av koden lettere.

## Import "as"

Vi kan også bruke `as` til å importere under forskjellige alias.
For eksempel, la oss importere `siHei` inn i den lokale variabelen `hei` for korthet i koden, og det samme for `siFarvel`:

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

Nå er `hi` og `goodbye` offisielle navn for parter utenfor:

```js
// 📁 main.js
import * as say from './say.js';

say.hi('John'); // Hi, John!
say.goodbye('John'); // Goodbye, John!
```

## export default

Så langt har vi sett på hvordan man importerer/eksporterer flere ting, valgfritt som (`as`) andre navn.

I praksis, modulere inneholder enten:
- Et bibliotek, samling av funksjoner, som `lib.js`.
- Eller et objekt som `class User` er beskrevet i `user.js`, hele modulen har kun denne klassen.

Som oftest, er den andre måten å ta ibruk foretrukket, sånn at hver "ting" oppholdes i sin egen modul.

Naturligvis, dette krever en hel del filer, som alle vil ha sin egen modul, men dette er ikke et problem. Faktisk, så blir navigering av kodebasen lettere, hvis filene er gitt bra navn og strukturert godt i egne mapper.

Moduler gir spesielle `export default` syntaks for å gjøre at "en ting per modul" ser bedre ut.

Det krever følgende `export` og `import` uttrykk:

1. Legg `export default` før "hoved eksporten" i modulen.
2. Kall `import` uten krøllparenteser.

For eksempel, her `bruker.js` exports `class Bruker`:

```js
// 📁 user.js
export *!*default*/!* class User { // kun tilføy "default"
  constructor(name) {
    this.name = name;
  }
}
```

...Og `main.js` importerer det:

```js
// 📁 main.js
import *!*User*/!* from './user.js'; // ikke {User}, kun User
new User('John');
```

Importsetninger uten krøllparentes ser finere ut. En vanlig feil når man begynner å bruke moduler er å glemme krøllparentes helt. Så, husk, `import` trenger krøllparentes for navngitte importsetninger og trenger dem ikke ikke default import.

| Navngitt export | Default export |
|--------------|----------------|
| `export class User {...}` | `export default class User {...}` |
| `import { User } from ...` | `import User from ...`|

Naturligvis kan det kun være en "default" export per fil.

Vi kan ha både default og navngitt eksporteringer i en enkelt modul, men i praksis vil folk blande disse to. En modul har enten navngitte eksporteringer eller en default.

**En annen ting å bite seg merke i er at navngitt eksporteringer må (naturligvis) ha et navn, mens `export default` kan være anonym.**

For eksempel, disse er alle helt gyldige eksporteringer:

```js
export default class { // ingen klassenavn
  constructor() { ... }
}

export default function(user) { // ingen funksjonsnavn
  alert(`Hi, ${user}!`);
}

// eksporter en enkelt verdi, uten å definere en variabel
export default ['Jan', 'Feb', 'Mar','Apr', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
```

Det går helt fint, fordi `export default` finnes det kun en av per fil, så `import` vet alltid hva som skal importeres.
 I motsetning til det, og utelater et navn for navngitte importeringer ville vært en feil i koden:

```js
export class { // Feil! (ikke-default eksportering trenger et navn)
  constructor() {}
}
```

### "Default" alias

Stikkordet "default" er et slags alias for default export, for når vi trenger å angi en referanse for den. 

For example, if we already have a function declared, that's how to `export default` it:
For eksempel, når vi allerede har deklarert en funksjon, er dette hvordan `export default` den:

```js
function sayHi(user) {
  alert(`Hi, ${user}!`);
}

export {sayHi as default}; // samme som hvis vi hadde lagt til "export default" før funksjonen
```

Eller, la oss si at modulen `user.js` eksporterer en hoved "default" ting og et par navngitte noen (sjeldent tilfelle, men skjer av og til):

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

Eller hvis vi vurderer å importere `*` som et objekt, da må `default` egenskapen være eksagt default export:

```js
// 📁 main.js
import * as User from './user.js';

let User = user.default;
new User('John');
```

### Burde jeg bruker default exports?

Vi må være forsiktige når vi bruker default exports, fordi disse kan være til en viss grad veldig annerledes å vedlikeholde.

Navngitte exports er eksplisitte. De navngir eksagt hva de importerer, slik at vi har den informasjonen når vi importerer de, Det er en bra ting.

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

```js
import User from './user.js';
import LoginForm from './loginForm.js';
import func from '/path/to/func.js';
...
```

En annen løsning ville vært å bruke navngitte exports overalt. Til og med hvis kun en enkelt fil er eksportert, er den fremdeles eksportert under et navn, uten `default`.

Dette gjør også re-export (se under) litt enklere å forstå.

## Re-export

"Re-export" syntaks `export ... from ...` lar ss importere ting og med en eksportere de (også mulig under andre navn enn importert), slik:


```js
export { sayHi } from './say.js';
export { default as User } from './user.js';
```

Hva er poenget, hvorfor trenger vi dette? La oss se på et praktisk bruksområde.

Se for deg, vi skriver en "pakke": en mappe med mange moduler, mest til bruk internt, med noe funksjonalitet eksportert utad (verktøy som NPM lar oss publisere og distribuere pakker, men det har ikke noe å si her).

En mappestruktur kan være slik:
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

Ideen er at parter fra utsiden, utviklere som bruker pakken vår, ikke bør tenke på dens interne struktur. De skal ikke måtte lete etter filer inne i vår pakke. Vi eksportert kun det som er nødvendig gjennom `auth/inde.js` og holder resten skjult fra nysgjerrige øyne

Nå som den faktiske eksporterte funksjonaliteten er spredt blant pakken, kan vi samle og "re-export" den i `auth/index.js`:

```js
// 📁 auth/index.js
import {login, logout} from './helpers.js';
export {login, logout};

import User from './user.js';
export {User};

import Github from './providers/github.js';
export {Github};
...
```

"Re-eksportering" er bare en måte å gjøre slik på:

```js
// 📁 auth/index.js
export {login, logout} from './helpers.js';
// or, to re-export all helpers, we could use:
// export * from './helpers.js';

export {default as User} from './user.js';

export {default as Github} from './providers/github.js';
...
```

````warn header="Re-eksporering default kan være vrient" 
Vær grei å merk: `export User from './user.js'` vill ikke virke. Dette er faktisk en syntaks feil. For å re-export en default export, må vi referensere den eksplisitt slik som `{default as ...}`, slik som eksempelet over.

I tillegg, er det en annen særhet: `export * from './user.js'` re-exports er kun navngitte eksporteringer, ekskludert standard eksport. Men igjen, vi må nevne den eksplisitt.

For eksempel, for å re-export alt, trenger vi to uttrykk:
```js
export * from './module.js'; // to re-export named exports
export {default} from './module.js'; // to re-export default
```

Standarden burde være nevnt eksplisitt kun når man re-eksporterer: `import * as obj` virker fint. Dette importerer en standard export som `obj.default`. Slik at det er en liten asymmetry mellom import og export konstruksjoner her.
````

## Sammendrag

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

We can put import/export statements below or after other code, that doesn't matter.

Så dette er teknisk rett:
```js
sayHi();

import {sayHi} from './say.js'; // import på slutten av filen
```

I praksis så er imports vanligvis deklarert i begynnelsen av hver enkelt filt, men det er kun av praktiske årsaker.

**Vær grei å legg merke til at import/export uttrykk ikke vil hvis de er plasser inne i `{...}`.**

Betinget import, som dette vil ikke fungere:
```js
if (something) {
  import {sayHi} from "./say.js"; // Feil: import må være på øverste nivå i modulen.
}
```

...Men hva hvis vi virkelig trenger å  importere noe basert på en betingelse? Eller på riktig tidspunkt i koden? Slik som, laste inn en modul på forespørsel, når den virkelig trengs?

Vi skal se på dynamiske import i neste kapittel.
