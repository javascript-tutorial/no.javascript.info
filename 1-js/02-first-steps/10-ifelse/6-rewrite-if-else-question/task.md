importance: 5

---

# Gjør om 'if..else' til '?'

Gjør om `if..else` påstanden under ved bruk av spørsmålstegn `'?'`.

Det er anbefalt å dele opp koden inn i flere linjer for bedre lesbarhet.

```js
let message;

if (login == "Employee") {
  message = "Hello";
} else if (login == "Director") {
  message = "Greetings";
} else if (login == "") {
  message = "No login";
} else {
  message = "";
}
```
