importanță: 5

---

# Rescrie "switch"-ul într-un "if"

Scrie codul folosind `if..else` care ar corespunde următorului `switch`:

```js
switch (browser) {
  case 'Edge':
    alert( "You've got the Edge!" );
    break;

  case 'Chrome':
  case 'Firefox':
  case 'Safari':
  case 'Opera':
    alert( 'Okay we support these browsers too' );
    break;

  default:
    alert( 'We hope that this page looks ok!' );
}
```