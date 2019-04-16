Pentru a egala cu precizie funcționalitatea lui `switch`, `if` trebuie să folosească o comparație strictă `'==='`.

Însă pentru string-uri date, un simplu `'=='` funcționează de asemenea.

```js no-beautify
if(browser == 'Edge') {
  alert("You've got the Edge!");
} else if (browser == 'Chrome'
 || browser == 'Firefox'
 || browser == 'Safari'
 || browser == 'Opera') {
  alert( 'Okay we support these browsers too' );
} else {
  alert( 'We hope that this page looks ok!' );
}
```

Te rog observă : construcția `browser == 'Chrome' || browser == 'Firefox' …` este ruptă în linii multiple pentru o lizibilitate mai mare.

Dar `switch`-ul este totuși mai curat și mai descriptiv.