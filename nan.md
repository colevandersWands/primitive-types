# NaN

careful of NaN, it's strange.  The simplest way to check if something is NaN is to compare it to itself (```x !== x```), NaN is the only value that will fail this comparison;

## Index
* [just NaN](#just-nan)
* [comparing to NaN](#comparing-to-nan)
* [isNaN](#isnan)
* [resources](#resources)

---

## Just NaN

[on pytut](http://www.pythontutor.com/live.html#code=/*%0A%20%20NaN,%20anything%20else%0A*/%0Aconst%20a%20%3D%20%3B%0Aconst%20expected%20%3D%20%3B%0A%0Alet%20result%3B%0Aif%20%28a%20!%3D%3D%20a%29%20%7B%0A%20%20result%20%3D%20'a%20is%20NaN'%3B%0A%7D%20else%20%7B%0A%20%20result%20%3D%20'a%20is%20not%20NaN'%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20result%29&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{
  /*
    NaN, anything else
  */
  const a = ;
  const expected = "";

  let path;
  if (a !== a) {
    path = 'a is NaN';
  } else {
    path = 'a is not NaN'
  }

  console.log("a: "+typeof a+", "+a);
  console.assert(expected === path, "path === " + path);
}
```

[TOP](#nan)

---

## Comparing to NaN

[on pytut](http://www.pythontutor.com/live.html#code=/*%0A%20%20NaN,%20anything%20else%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20expected%20%3D%20%3B%0A%0Alet%20path%3B%0Aif%20%28a%20%3D%3D%3D%20b%29%20%7B%0A%20%20path%20%3D%20'the%20same%20%26%20not%20NaN'%3B%20%20%0A%7D%20else%20if%20%28%20%28a%20!%3D%3D%20a%29%20%26%26%20%28b%20!%3D%3D%20b%29%20%29%20%7B%0A%20%20path%20%3D%20'both%20are%20NaN'%3B%0A%7D%20else%20%7B%0A%20%20path%20%3D%20'different%20values'%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20path,%20%22path%20%3D%3D%3D%20%22%20%2B%20path%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{
  /*
    NaN, anything else
  */
  const a = , b = ;
  const expected = "";

  let path;
  if (a === b) {
    path = 'the same & not NaN';  
  } else if ( (a !== a) && (b !== b) ) {
    path = 'both are NaN';
  } else {
    path = 'different values'
  }

  console.log("a: "+typeof a+", "+a);
  console.log("b: "+typeof b+", "+b);
  console.assert(expected === path, "path === " + path);
}
```

[TOP](#nan)

---

### isNaN

```isNaN``` and ```Number.isNaN``` are functions built into JS that check to see if a value is ```NaN```.   They are different in a subtle but very important way:
* ```Nimber.isNaN``` checks if a value is ```NaN``` __WITHOUT__ [converting that value to a number](#number)
* ```isNaN``` checks if a value is ```NaN``` __AFTER__ [converting that value to a number](#number)


[on pytut](http://www.pythontutor.com/live.html#code=/*%0A%20%20NaN,%20%22letters%22,%20null,%20undefined,%20%223%22%0A%20%22Infinity%22,%20%22NaN%22,%20true,%20false,%20%223e4%22%0A*/%0Aconst%20a%20%3D%20%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Aconst%20a_to_number%20%3D%20Number%28a%29%3B%0Aconst%20number_is_nan%20%3D%20Number.isNaN%28a%29%3B%0Aconst%20is_nan%20%3D%20isNaN%28a%29%3B%0A%0Alet%20actual%3B%0Aif%20%28number_is_nan%20%3D%3D%3D%20is_nan%29%20%7B%0A%20%20actual%20%3D%20'they%20agree'%3B%0A%7D%20else%20%7B%0A%20%20actual%20%3D%20'they%20dont%20agree'%0A%7D%0A%0Aconsole.log%28%22a%3A%20%22%2Btypeof%20a%2B%22,%20%22%2Ba%29%3B%0Aconsole.log%28%22Number%28a%29%3A%20%22%2Btypeof%20a_to_number%2B%22,%20%22%2Ba_to_number%29%3B%0Aconsole.log%28%22isNaN%28a%29%3A%20%22%2Bis_nan%29%0Aconsole.log%28%22Number.isNaN%28a%29%3A%20%22%2Bnumber_is_nan%29%0Aconsole.assert%28expected%20%3D%3D%3D%20actual,%20%22actual%20%3D%3D%3D%20%22%20%2B%20actual%29%3B&cumulative=false&curInstr=27&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{
  /*
    NaN, "letters", null, undefined, "3"
   "Infinity", "NaN", true, false, "3e4"
  */
  const a = ;
  const expected = "";
  
  const number_is_nan = Number.isNaN(a);
  const is_nan = isNaN(a);

  let actual;
  if (number_is_nan === is_nan) {
    actual = 'they agree';
  } else {
    actual = 'they dont agree'
  }
  
  const a_to_number = Number(a);

  console.log("a: "+typeof a+", "+a);
  console.log("Number(a): "+typeof a_to_number+", "+a_to_number);
  console.log("isNaN(a): "+is_nan)
  console.log("Number.isNaN(a): "+number_is_nan)
  console.assert(expected === actual, "actual === " + actual);
}
```

> can you describe in general terms when these operators will agree? 
> (ie. both are false when ..., both are true when ..., they do not agree when ...


[TOP](#nan)

---

## Resources

* [MDN: NaN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN)
* [MDN: isNaN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/isNaN)
* [testing for NaN](http://adripofjavascript.com/blog/drips/the-problem-with-testing-for-nan-in-javascript.html)
* [NaN explained](https://javascriptrefined.io/nan-and-typeof-36cd6e2a4e43)

[TOP](#nan)

___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>

