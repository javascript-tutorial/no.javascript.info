<<<<<<< HEAD
# Operant betinging: if, '?'
=======
# Conditional branching: if, '?'
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b

Ofte i koden vår ønsker vi å utføre forskjellige operasjoner basert på ulike betingelser.

<<<<<<< HEAD
For å bestemme hvilken kode som skal bli kjørt basert disse ulike betingelsene, bruker vi noe som kalles for "if" påstand (eng: if-statement). Man kan også benytte seg av en (ternary) operator, som vi vil skrive mer om etterpå.
=======
To do that, we can use the `if` statement and the conditional operator `?`, that's also called a "question mark" operator.
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b

## "if" påstand

<<<<<<< HEAD
Oppgaven til en `if` påstand er å evaluere en betingelse (condition). Om resultatet er sant (`true`) kjøres koden.
=======
The `if(...)` statement evaluates a condition in parentheses and, if the result is `true`, executes a block of code.
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b

Eksempel:

```js run
let year = prompt('In which year was ECMAScript-2015 specification published?', '');

*!*
if (year == 2015) alert( 'You are right!' );
*/!*
```

Ofte ønsker man å kjøre flere liner med kode om en betingelse er sann. For å gjøre dette pakker vi koden inn i krøllparantes (curly brackets) - `{}`.

```js
if (year == 2015) {
  alert("That's correct!");
  alert("You're so smart!");
}
```

En god tommelfingerregel er å alltid pakke koden etter en "if" påstand inn i krøllparanteser. Dette gjør koden både mer konsekvent og lettere å lese.

## Boolsk (boolean) "oversettelse"

Hver gang en `if (…)` påstand evaluerer betingelsen, gjør den koden inni om til en boolsk verdi.

La oss friske opp hukommelsen med true/false oversettelsene fra kapittelet <info:type-conversions>:

- Tallet `0`, en tom tekst `""`, `null`, `undefined`, og `NaN` blir alle omgjort til `false`. De kalles for "falsy" verdier.
- Alle andre verdier blir `true`, og kalles passende nok for "truthy" verdier.

Med denne kunnskapen, vet vi nå at koden under aldri vil bli kjørt:

```js
if (0) { // 0 is falsy
  ...
}
```

...mens denne koden alltid vil bli kjørt:

```js
if (0) { // 0 is falsy
  ...
}
```

Det er også lov å sette inn en allerede evaluert boolsk verdi inn i en `if` påstand:

```js
let cond = (year == 2015); // equality evaluates to true or false

if (cond) {
  ...
}
```

## Else "leddsetningen"

Det hender at man ofte vil kjøre én spesifikk kode hvis betingelsen i "if" påstanden stemmer, og ellers en annen kode hvis den ikke stemmer. For å gjøre dette bruker man noe som kalles for en "else statement". Denne kjøres uansett hvis "if" påstanden er false.

<<<<<<< HEAD
Eksempel:
=======
The `if` statement may contain an optional "else" block. It executes when the condition is falsy.
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b

```js run
let year = prompt(
  "In which year was the ECMAScript-2015 specification published?",
  ""
);

if (year == 2015) {
  alert("You guessed it right!");
} else {
  alert("How can you be so wrong?"); // any value except 2015
}
```

## Flere påstander: "else if"

Noen ganger ønsker man å teste flere betingelser. For å gjøre dette bruker vi `else if` påstander.

For eksempel:

```js run
let year = prompt(
  "In which year was the ECMAScript-2015 specification published?",
  ""
);

if (year < 2015) {
  alert("Too early...");
} else if (year > 2015) {
  alert("Too late");
} else {
  alert("Exactly!");
}
```

Fremgangsmåten til JavaScript er å først sjekke om `alder == 18)`. Hvis det er "falsy", sjekker den neste påstand som er `alder < 18`. Hvis denne viser seg også å være "falsy", kjører den koden som er i "else" påstanden.

Merk: Det kan være flere `else if` påstander, men bare en `else` påstand.

<<<<<<< HEAD
## Ternary operatør '?'
=======
## Conditional operator '?'
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b

Det hender at man ønsker å sette en variabel basert på en betingelse.

For eksempel:

```js run no-beautify
let accessAllowed;
let age = prompt('How old are you?', '');

*!*
if (age > 18) {
  accessAllowed = true;
} else {
  accessAllowed = false;
}
*/!*

alert(accessAllowed);
```

<<<<<<< HEAD
For å gjøre dette på en enklere måte, kan vi bruke noe som heter "ternary operator". Noen kaller denne også for "question mark operator".

Dettte er fordi denne operatøren brukes med et `?`-tegn. "Ternary" betyr at operatøren har tre "operander", som er tegnene som brukes i uttrykket. Denne er faktisk den eneste operatøren i JavaScript som har tre operander.

Syntaksen er som følger:
=======
The so-called "conditional" or "question mark" operator lets us do that in a shorter and simpler way.

The operator is represented by a question mark `?`. Sometimes it's called "ternary", because the operator has three operands. It is actually the one and only operator in JavaScript which has that many.
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b

```js
let result = condition ? value1 : value2;
```

`Betingelsen` blir evaluert, og hvis den er "truthy" blir `verdi1`returnet, hvis ikke blir `verdi2` returnert.

For eksempel:

```js
let accessAllowed = age > 18 ? true : false;
```

<<<<<<< HEAD
Teknisk sett kan vi sette paranteser rundt `alder > 18`. Men spørsmålstegnet i en ternary operatør har en lav rang, og vil dermed bli kjørt etter `>`-sjekken.
=======
Technically, we can omit the parentheses around `age > 18`. The question mark operator has a low precedence, so it executes after the comparison `>`.
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b

Dette eksemplet vil fungere likt som det forrige:

```js
// the comparison operator "age > 18" executes first anyway
// (no need to wrap it into parentheses)
let accessAllowed = age > 18 ? true : false;
```

Allikevel anbefales det å bruke paranteser selv om det ikke er nødvendig, ettersom det gjør koden lettere å lese.

````smart
Merk: I eksempelet over hadde man egentlig ikke trengt å benytte seg av ternary operatøren, ettersom sjekken ville returnet `true/false` av seg selv.

```js
// the same
let accessAllowed = age > 18;
```
````

## Flere '?' på rad

Det er mulig å benytte seg av flere spørsmålstegn `?` for å returnere en verdi som baserer seg på flere betingelser.

For eksempel:

```js run
let age = prompt("age?", 18);

let message =
  age < 3
    ? "Hi, baby!"
    : age < 18
    ? "Hello!"
    : age < 100
    ? "Greetings!"
    : "What an unusual age!";

alert(message);
```

Det kan vøre uvant å forstå hva som foregår her med en gang. Tar vi en nærmere kikk derimot, ser vi at det bare er flere sekvenser med betingelser:

1. Det første spørsmålstegnet sjekker om `age < 3`.
2. Om det er "true" returnerer den `'Hi, baby!'`. Hvis den ikke er "true", går den til neste verdien etter kolontegenet '":"', som er `age < 18`.
3. Om det "true", returner den `'Hello!'`. Hvis den ikke er "true", går den til neste verdien etter kolontegenet '":"', som er `age < 100`.
4. Om det "true", returner den `'Greetings!'`. Hvis den ikke er "true", går den til neste verdien etter kolontegenet '":"', som er `'What an unusual age!'`.

Her kan du se hvordan det ville sett ut med `if..else`:

```js
if (age < 3) {
  message = "Hi, baby!";
} else if (age < 18) {
  message = "Hello!";
} else if (age < 100) {
  message = "Greetings!";
} else {
  message = "What an unusual age!";
}
```

## Utradisjonell bruk av '?'

Det hender at spørsmålstegnet `?` blir brukt som et alternativ for `if`:

```js run no-beautify
let company = prompt('Which company created JavaScript?', '');

*!*
(company == 'Netscape') ?
   alert('Right!') : alert('Wrong.');
*/!*
```

Avhengig om påstanden `selskap == 'Netscape` stemmer eller ikke, vil enten den første eller andre koden etter `?` bli kjørt.

Her satt vi ikke resultatet til en variabel, men kjørte forskjellig kode avhengig av påstanden.

<<<<<<< HEAD
**Vi anbefaler ikke at man bruker spørsmålstegnet på denne måten.**
=======
**It's not recommended to use the question mark operator in this way.**
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b

Å skrive det på denne måten er kortere enn en `if` påstand, som kan være attraktivt for mange programmerere. Men det er vanskeligere å lese, og sees dermed på som dårlig vane.

Her kan du sammenligne den samme koden med en `if` påstand:

```js run no-beautify
let company = prompt('Which company created JavaScript?', '');

*!*
if (company == 'Netscape') {
  alert('Right!');
} else {
  alert('Wrong.');
}
*/!*
```

Her leser øynene våre lodrett kode istedenfor lange, vannrette linjer med kode. Dette er en bedre og mer behagelig standard for programmere å håndtere.

Meningen med å bruke spørsmålstegnet `?` er å returnere verdier til variabler basert på en betingelse. Vennligst bruk den kun for det, og ellers bruk `if` når du skal kjøre flere forskjellige blokker med kode.
