importance: 5

---

# Gjør om 'if..else' til '?'

Gjør om `if..else` påstanden under ved bruk av spørsmålstegn `'?'`.

Det er anbefalt å dele opp koden inn i flere linjer for bedre lesbarhet.

```js
let melding;

if (login == "Ansatt") {
  melding = "Hallo";
} else if (login == "Direktør") {
  melding = "God dag";
} else if (login == "") {
  melding = "Ingen login";
} else {
  melding = "";
}
```
