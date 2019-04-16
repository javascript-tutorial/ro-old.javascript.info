Primele două validări se transformă în două `case`-uri. A treia verificare este ruptă în două cazuri:

```js run
let a = +prompt('a?', '');

switch (a) {
  case 0:
    alert( 0 );
    break;

  case 1:
    alert( 1 );
    break;

  case 2:
  case 3:
    alert( '2,3' );
*!*
    break;
*/!*
}
```

Te rog observă că: `break`-ul de la sfârșit nu este necesar. Dar îl punem pentru a face codul mai stabil în viitor.

În viitor se poate să vrem să adăugăm una sau mai multe ramuri `case`, spre exemplu `case 4`. Și dacă uităm să adăugăm un break înainte de el, la sfârșitul lui `case 3`, va exista o eroare. Așadar acest lucru este un fel de auto-asigurare.