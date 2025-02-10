# Den moderne JavaScript Opplæringsdelen på Norsk

Dette oppbevaringsstedet er vertsplass for oversettelsen av <https://javascript.info> på Norsk.


**Slik kan du bidra:**

<<<<<<< HEAD
- Sjekk ut [Den Norske Oversettelses fremdriften](https://github.com/javascript-tutorial/no.javascript.info/issues/1) issue.
- Velg en umarkert artikkel du har lyst til å oversette.
- Legg til en kommentar ved artikkelens navn i issue, f.eks `An Introduction to JavaScript`.
    - Bot'en vår vil markere denne issue, så alle kan se at du jobber med å oversette den.
    - Kommentaren din skal kun inneholde tittelen.
- Fork dette repository, oversett artikkelen og send en PR når du er ferdig.
    - PR tittel burde være lik tittelen til artikkelen du oversetter, bot'en vil skrive nummeret til issue.
    
Vær grei å la vedlikeholdere gå gjennom og merge, eller foreslå endringer i oversettelsen din.
=======
See <https://javascript.info/translate> for the details.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

Hvis vedlikeholdere ikke svarer, eller du har lyst til å bli en vedlikeholder, kontakt oss i [hovedrepoet](https://github.com/javascript-tutorial/en.javascript.info/issues/new).

**La andre få vite hva du oversetter, i meldingbordet, eller chat på ditt språk. Inviter de til å bli med!**

<<<<<<< HEAD
🎉 Tusen takk!

Ditt navn og størrelsen på ditt bidrag vil dukke opp i "om prosjekt" delen av nettsiden når dette blir publisert.
=======
Something's wrong? A topic is missing? Explain it to people, add it as PR 👏

**You can edit the text in any editor.** The tutorial uses an enhanced "markdown" format, easy to grasp. And if you want to see how it looks on-site, there's a server to run the tutorial locally at <https://github.com/javascript-tutorial/server>.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

P.S. Hele listen av språk kan finnes her <https://javascript.info/translate>.

## Struktur

<<<<<<< HEAD
Hvert kapittel, en artikkel eller oppgave holder til i sin egen mappe.

Mappen sitt har navnet `N-url`, hvor `N` - står for nummer for hvordan (artiklene organiseres), og `url` er URL-stien på siden.
=======
Every chapter, article, or task has its folder.

The folder is named like `N-url`, where `N` is a number for the sorting purposes and `URL` is the URL part with the title of the material.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

Hver mappe har en av følgende filer:

<<<<<<< HEAD
- `index.md` for en seksjon,
- `article.md` for en artikkel,
- `task.md` for en oppgave (+`solution.md` med løsningsteksten hvis det finnes en).
=======
  - `index.md` stands for a chapter
  - `article.md` stands for an article
  - `task.md` stands for a task (solution must be provided in `solution.md` file as well)
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

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

### Eksterne linker

Hvis en ekstern lenke fører til Wikipedia, f.eks `https://en.wikipedia.org/wiki/JavaScript`, og en versjon av den artikkelen eksisterer på ditt språk, og er av god kvalitet kan det lenkes til den artikkelen istedenfor.

Eksempel:

```md
[JavaScript](https://en.wikipedia.org/wiki/JavaScript) is a programming language.
```

✅ OK (en -> no):

```md
[JavaScript](https://no.wikipedia.org/wiki/JavaScript) er et programmeringsspråk.
```

Når det gjelder lenker til MDN, er en delvis oversatt artikkel ok.

Hvis det er lenket til en artikkel som ikke har en oversatt versjon, la den originale lenken være som den er.

### Metadata

Noen filer, vanligvis oppgaver, har YAML metadata definert i toppen, markert med `---`:

```md
importance: 5

<<<<<<< HEAD
---
...
```

Vennligst ikke oversett "importance" (og andre metadata definert i toppen).

### Ankerpunkter

Noen overskrifter har `[#anchor]` på slutten, f.eks.

```md
## Spread operator [#spread-operator]
```

Vennligst ikke oversett eller fjern `[#...]` delen, dette er for URL ankerpunkter.

## Kjøring lokalt

Du kan kjøre opplæringsdelens server lokalt for å se hvordan oversettelsene dine ser ut.

Serveren og installasjonsinstrukser kan finnes her: <https://github.com/javascript-tutorial/server>. 
=======
---  
♥  
Ilya Kantor @iliakan
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e
