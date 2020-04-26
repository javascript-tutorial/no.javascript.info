# Operant betinging: if, '?'

Ofte i koden vår ønsker vi å utføre forskjellige operasjoner basert på ulike betingelser.

For å bestemme hvilken kode som skal bli kjørt basert disse ulike betingelsene, bruker vi noe som kalles for "if" påstand (eng: if-statement). Man kan også benytte seg av en (ternary) operator, som vi vil skrive mer om etterpå.

## "if" påstand

Oppgaven til en `if` påstand er å evaluere en betingelse (condition). Om resultatet er sant (`true`) kjøres koden.

Eksempel:

```js run
let perAlder = 20

*!*
if (perAlder > 19) alert("Per ikke er en tenåring lengre!");
*/!*
```

Ofte ønsker man å kjøre flere liner med kode om en betingelse er sann. For å gjøre dette pakker vi koden inn i krøllparantes (curly brackets) - `{}`.

```js
if (perAlder > 19) {
  alert("Per ikke er en tenåring lengre!");
  alert("Nå er han en ung voksen.");
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
if (0) { // 0 er "falsy"
  ...
}
```

...mens denne koden alltid vil bli kjørt:

```js
if (1) { // 1 er "truthy"
  ...
}
```

Det er også lov å sette inn en allerede evaluert boolsk verdi inn i en `if` påstand:

```js
let myndig = (alder == 17); // dobbel likhetstegn evaluerer true eller false

if (myndig) {
  ...
}
```

## Else "leddsetningen"

Det hender at man ofte vil kjøre én spesifikk kode hvis betingelsen i "if" påstanden stemmer, og ellers en annen kode hvis den ikke stemmer. For å gjøre dette bruker man noe som kalles for en "else statement". Denne kjøres uansett hvis "if" påstanden er false.

Eksempel:

```js run
let alder = prompt("Hva er laveste aldersgrensen for å kjøre bil?", "");

if (alder == 18) {
  alert("Helt korrekt!");
} else {
  alert("Beklager, der tok du feil."); // alle verdier utenom 18
}
```

## Flere påstander: "else if"

Noen ganger ønsker man å teste flere betingelser. For å gjøre dette bruker vi `else if` påstander.

For eksempel:

```js run
let alder = prompt("Hva er laveste aldersgrensen for å kjøre bil?", "");

if (alder == 18) {
  alert("Helt korrekt!");
} else if (alder < 18) {
  alert("Da er du for ung");
} else {
  alert("Ikke laveste aldersgrense!");
}
```

Fremgangsmåten til JavaScript er å først sjekke om `alder == 18)`. Hvis det er "falsy", sjekker den neste påstand som er `alder < 18`. Hvis denne viser seg også å være "falsy", kjører den koden som er i "else" påstanden.

Merk: Det kan være flere `else if` påstander, men bare en `else` påstand.

## Ternary operatør '?'

Det hender at man ønsker å sette en variabel basert på en betingelse.

For eksempel:

```js run no-beautify
let tilgang;
let alder = prompt('Hvor galmmel er du?', '');

*!*
if (alder > 18) {
  tilgang = true;
} else {
  tilgang = false;
}
*/!*

alert(tilgang);
```

For å gjøre dette på en enklere måte, kan vi bruke noe som heter "ternary operator". Noen kaller denne også for "question mark operator".

Dettte er fordi denne operatøren brukes med et `?`-tegn. "Ternary" betyr at operatøren har tre "operander", som er tegnene som brukes i uttrykket. Denne er faktisk den eneste operatøren i JavaScript som har tre operander.

Syntaksen er som følger:

```js
let resultat = betingelse ? verdi1 : verdi2;
```

`Betingelsen` blir evaluert, og hvis den er "truthy" blir `verdi1`returnet, hvis ikke blir `verdi2` returnert.

For eksempel:

```js
let tilgang = alder > 18 ? true : false;
```

Teknisk sett kan vi sette paranteser rundt `alder > 18`. Men spørsmålstegnet i en ternary operatør har en lav rang, og vil dermed bli kjørt etter `>`-sjekken.

Dette eksemplet vil fungere likt som det forrige:

```js
// sjekken "alder > 18" vil bli kjørt først uansett
// (så det er ingen grunn til å pakke den inn i parantes)
let tilgang = alder > 18 ? true : false;
```

Allikevel anbefales det å bruke paranteser selv om det ikke er nødvendig, ettersom det gjør koden lettere å lese.

````smart
Merk: I eksempelet over hadde man egentlig ikke trengt å benytte seg av ternary operatøren, ettersom sjekken ville returnet `true/false` av seg selv.

```js
// samme som over
let tilgang = alder > 18;
```
````

## Flere '?' på rad

Det er mulig å benytte seg av flere spørsmålstegn `?` for å returnere en verdi som baserer seg på flere betingelser.

For eksempel:

```js run
let alder = prompt("alder?", 18);

let melding =
  alder < 3
    ? "Hei spedbarn!"
    : age < 18
    ? "Hallo!"
    : age < 100
    ? "God dag!"
    : "For en høy alder!";

alert(melding);
```

Det kan vøre uvant å forstå hva som foregår her med en gang. Tar vi en nærmere kikk derimot, ser vi at det bare er flere sekvenser med betingelser:

1. Det første spørsmålstegnet sjekker om `alder < 3`.
2. Om det er "true" returnerer den `'Hei spedbarn!'`. Hvis den ikke er "true", går den til neste verdien etter kolontegenet '":"', som er `alder < 18`.
3. Om det "true", returner den `'Hallo!'`. Hvis den ikke er "true", går den til neste verdien etter kolontegenet '":"', som er `age < 100`.
4. Om det "true", returner den `'God dag!'`. Hvis den ikke er "true", går den til neste verdien etter kolontegenet '":"', som er `'What an unusual age!'`.

Her kan du se hvordan det ville sett ut med `if..else`:

```js
if (alder < 3) {
  melding = "Hei spedbarn!";
} else if (alder < 18) {
  melding = "Hallo!";
} else if (alder < 100) {
  melding = "God dag!";
} else {
  melding = "For en høy alder!";
}
```

## Utradisjonell bruk av '?'

Det hender at spørsmålstegnet `?` blir brukt som et alternativ for `if`:

```js run no-beautify
let selskap = prompt('Hvilket selskap lagde JavaScript?', '');

*!*
(selskap == 'Netscape') ?
   alert('Stemmer!') : alert('Feil.');
*/!*
```

Avhengig om påstanden `selskap == 'Netscape` stemmer eller ikke, vil enten den første eller andre koden etter `?` bli kjørt.

Her satt vi ikke resultatet til en variabel, men kjørte forskjellig kode avhengig av påstanden.

**Vi anbefaler ikke at man bruker spørsmålstegnet på denne måten.**

Å skrive det på denne måten er kortere enn en `if` påstand, som kan være attraktivt for mange programmerere. Men det er vanskeligere å lese, og sees dermed på som dårlig vane.

Her kan du sammenligne den samme koden med en `if` påstand:

```js run no-beautify
let selskap = prompt('Hvilket selskap lagde JavaScript?', '');

*!*
if (company == 'Netscape') {
  alert('Stemmer!');
} else {
  alert('Feil.');
}
*/!*
```

Her leser øynene våre lodrett kode istedenfor lange, vannrette linjer med kode. Dette er en bedre og mer behagelig standard for programmere å håndtere.

Meningen med å bruke spørsmålstegnet `?` er å returnere verdier til variabler basert på en betingelse. Vennligst bruk den kun for det, og ellers bruk `if` når du skal kjøre flere forskjellige blokker med kode.
