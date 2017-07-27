# Convert an ascii string to a integer
> A common interview question is to write  a function that converts  a  string into an integer e.g. `"123"` => `123`.  This function is commonly called  atoi because  we  are converting  an ASCII string into an integer.

> In this lesson we cover the proper way to do this in JavaScript which is `parseInt` along with implementing it using basic ascii math.

A common interview question is to write a function that takes a string returns and returns a number.

```js
/**
 * Converts a string to a integer
 * e.g. "123" => 123
 */
export function atoi(str: string): number {

}
```

JavaScript has a function called `parseInt`, that can do this integer parsing for us.

* For simple ints we get the int,
* For ints with a negative sign we get a negative int.
* When it encounters a character that is not a numeral, it ignores it and all succeeding characters. It still returns the integer value parsed up to that point.
* You can use this fact to ignore decimal portions as well.
* Finally if a string does not start with a decimal numeral it returns NaN i.e. Not A Number.

```js
/**
 * Converts a string to a integer
 * e.g. "123" => 123
 */
export function atoi(str: string): number {
  return parseInt(str);
}

console.log(atoi('123')); // 123
console.log(atoi('-123')); // -123
console.log(atoi('-123Extra')); // -123
console.log(atoi('-123.456')); // -123
console.log(atoi('Does not start with a digit 123')); // NaN
```

Note that `parseInt` siliently ignoring invalid trailing characters can be considered a problem. So a better implementation

```js
function atoi(value) {
  if (/^(\-|\+)?([0-9]+|Infinity)$/.test(value))
    return Number(value);
  return NaN;
}
```

Things that can go wrong:
* A good one worth mentioning is that we are assuming that the string is a valid integer to begin with. To check against that we would check that the result of this difference should be in range `0-9`.