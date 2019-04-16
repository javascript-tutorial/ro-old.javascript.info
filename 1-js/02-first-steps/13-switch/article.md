# Afirmația "switch"

O afirmație `switch` poate înlocui validări `if` multiple.

Aceasta oferă o modalitate mai descriptivă de a compara o valoare, cu variante multiple.

## Sintaxa

`switch`-ul are unul sau mai multe blocuri `case` și o opțiune default.

Arată astfel :

```js no-beautify
switch(x) {
  case 'value1':  // if (x === 'value1')
    ...
    [break]

  case 'value2':  // if (x === 'value2')
    ...
    [break]

  default:
    ...
    [break]
}
```

- Valoarea lui `x` este verificată pentru o egalitate strictă, relativ la valoarea din primul `case` (aceasta fiind `value1`), apoi relativ la cea de a doua (`value2`) ș.a.m.d.
- Dacă este egalitate `switch`-ul începe să execute codul de la respectivul `case`, până la cel mai apropiat `break` (sau până la sfârșitul `switch`-ului).
- Dacă nu se potrivește niciun caz atunci va fi executat codul de pe cazul `default` (dacă acesta există).

## Un exemplu

Un exemplu de `switch` (codul executat este scos în evidență):

```js run
let a = 2 + 2;

switch (a) {
  case 3:
    alert( 'Too small' );
    break;
*!*
  case 4:
    alert( 'Exactly!' );
    break;
*/!*
  case 5:
    alert( 'Too large' );
    break;
  default:
    alert( "I don't know such values" );
}
```

Aici `switch`-ul începe să-l compare pe `a` din prima variantă `case`, care este `3`. Potrivirea eșuează.

Apoi cu `4`. Există egalitate, așadar execuția începe de la `case 4` până la cel mai apropiat `break`.

**Dacă nu există niciun `break` atunci execuția continuă cu următorul `case`, fără nicio verificare.**

Un exemplu fără `break`:

```js run
let a = 2 + 2;

switch (a) {
  case 3:
    alert( 'Too small' );
*!*
  case 4:
    alert( 'Exactly!' );
  case 5:
    alert( 'Too big' );
  default:
    alert( "I don't know such values" );
*/!*
}
```

În exemplul de mai sus vom vedea execuția secvențială a 3 alert-uri:

```js
alert( 'Exactly!' );
alert( 'Too big' );
alert( "I don't know such values" );
```

````smart header="Any expression can be a `switch/case` argument"
Atât `switch` cât și `case` permit expresii arbitrare.

Spre exemplu:

```js run
let a = "1";
let b = 0;

switch (+a) {
*!*
  case b + 1:
    alert("this runs, because +a is 1, exactly equals b+1");
    break;
*/!*

  default:
    alert("this doesn't run");
}
```
Aici `+a` va da `1`, care este comparat cu `b + 1` în `case`, și este executat codul corespunzător.
````

## Gruparea lui "case"

Pot fi grupate câteva variante ale lui `case` care împart același cod.

Spre exemplu, dacă vrem ca același cod să ruleze pentru `case 3` și `case 5`:

```js run no-beautify
let a = 2 + 2;

switch (a) {
  case 4:
    alert('Right!');
    break;

*!*
  case 3:                    // (*) grouped two cases
  case 5:
    alert('Wrong!');
    alert("Why don't you take a math class?");
    break;
*/!*

  default:
    alert('The result is strange. Really.');
}
```

Acum atât `3` cât și `5` afișează același mesaj.

Abilitatea de a grupa cazuri este un efect secundar al modului în care `switch/case` funcționează fără `break`. Aici execuția lui `case 3` începe de la linia `(*)` și merge până la `case 5`, pentru că nu există niciun `break`.

## Tipul contează

Să accentuăm faptul că verificarea egalității este mereu strictă. Valorile trebuie să fie de același tip pentru a fi egale.

Spre exemplu, să luăm în considerare următorul cod:

```js run
let arg = prompt("Enter a value?")
switch (arg) {
  case '0':
  case '1':
    alert( 'One or zero' );
    break;

  case '2':
    alert( 'Two' );
    break;

  case 3:
    alert( 'Never executes!' );
    break;
  default:
    alert( 'An unknown value' )
}
```

1. Pentru `0`, `1` rulează primul `alert`.
2. Pentru `2` rulează cel de al doilea `alert`.
3. Dar pentru `3` rezultatul lui `prompt` este un string `"3"`, care nu este strict egal `===` cu numărul `3`. Așadar avem un cod mort în `case 3`! Va executa varianta `default`.