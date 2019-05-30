# Den moderne JavaScript Opplæringsdelen på Norsk

Dette oppbevaringsstedet er vertsplass for oversettelsen av <https://javascript.info> på Norsk.


**Slik kan du bidra:**

- Sjekk ut [Den Norske Oversettelses fremdriften](https://github.com/javascript-tutorial/no.javascript.info/issues/1) issue.
- Velg en umarkert artikkel du har lyst til å oversette.
- Legg til en kommentar ved artikkelens navn i issue, f.eks `An Introduction to JavaScript`.
    - Bot'en vår vil markere denne issue, så alle kan se at du jobber med å oversette den.
    - Kommentaren din skal kun inneholde tittelen.
- Fork dette repository, oversett artikkelen og send en PR når du er ferdig.
    - PR tittel burde være lik tittelen til artikkelen du oversetter, bot'en vil skrive nummeret til issue.
    
Vær grei å la vedlikeholdere gå gjennom og merge, eller foreslå endringer i oversettelsen din.

Hvis vedlikeholdere ikke svarer, eller du har lyst til å bli en vedlikeholder, kontakt oss i [hovedrepoet](https://github.com/javascript-tutorial/en.javascript.info/issues/new).

**La andre få vite hva du oversetter, i meldingbordet, eller chat på ditt språk. Inviter de til å bli med!**

🎉 Tusen takk!

Ditt navn og størrelsen på ditt bidrag vil dukke opp i "om prosjekt" delen av nettsiden når dette blir publisert.

P.S. Hele listen av språk kan finnes her <https://javascript.info/translate>.

## Struktur

Hvert kapittel, en artikkel eller oppgave holder til i sin egen mappe.

Mappen sitt har navnet `N-url`, hvor `N` - står for nummer for hvordan (artiklene organiseres), og `url` er URL-stien på siden.

Hver mappe har en av følgende filer:

- `index.md` for en seksjon,
- `article.md` for en artikkel,
- `task.md` for en oppgave (+`solution.md` med løsningsteksten hvis det finnes en).

En fil starter med `# Tittel overskrift`, og så er teksten skrevet i Markdown-lignende format, redigerbar i hvilken som helst text-editor.

tilleggsressurser og eksempler laget for artikkelen eller oppgaven, er alltid på samme mappenivå.

## Oversetningstips

Vær snill å hold linjeskift og avsnitt som de er: ikke legg til nye linjeskift og ikke fjern eksisterende linjeskift. Gjør det lettere for andre å slå sammen Pull requests i fremtiden.

Hvis du ser at den Norske versjonen kan forbedres - flott, send inn en PR til den.

### Vilkår

- Noen vilkårsspesifikasjoner skal ikke oversettes, f.eks "Function Declaration" kan være som "som den er".
- For andre stikkord som `resolved promise`, `slash`, `regexp`, og så videre - foreslår å slå opp en ordliste, hvis det finnes en passende oversettelse for Norsk. Hvis ikke, se etter oversettelser som finnes fra eksisterer i lignende brukermanual, som [MDN](https://developer.mozilla.org/en-US/).

### Tekst i Kodesnutter

- Oversett kommentarer.
- Oversett bruker-meldinger og eksempel stringverdier.
- Ikke oversett variabelnavn, klasser, identifikatorer
- Dobbelsjekk at koden fungerer etter at den er oversatt :)

Eksempel:

```js
// Example
const text = "Hello, world";
document.querySelector('.hello').innerHTML = text;
```

✅ OK (oversett kommentar):

```js
// Eksempel
const text = 'Hei, verden';
document.querySelector('.hello').innerHTML = text;
```

❌ IKKE OK (oversett klasse):

```js
// Eksempel
const text = 'Hei, verden';
// ".hello" er en klasse
// IKKE OVERSETT DETTE
document.querySelector('.hallo').innerHTML = text;
```

### External Links

If an external link is to Wikipedia, e.g. `https://en.wikipedia.org/wiki/JavaScript`, and a version of that article exists in your language that is of decent quality, link to that version instead.

Example:

```md
[JavaScript](https://en.wikipedia.org/wiki/JavaScript) is a programming language.
```

✅ OK (en -> es):

```md
[JavaScript](https://es.wikipedia.org/wiki/JavaScript) es un lenguaje de programación.
```

For links to MDN, a partially translated version is ok.

If a linked article has no translated version, leave the link "as is".

### Metadata

Some files, usually tasks, have YAML metadata at the top, delimited by `---`:

```md
importance: 5

---
...
```

Please don't translate "importance" (and other top metadata).

### Anchors

Some headers have `[#anchor]` at the end, e.g.

```md
## Spread operator [#spread-operator]
```

Please don't translate or remove the `[#...]` part, it's for URL anchors.

## Running locally

You can run the tutorial server locally to see how the translation looks.

The server and install instructions are at <https://github.com/javascript-tutorial/server>. 
