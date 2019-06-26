## Strict Comparisons

There are two strict comparison operators, ```===``` and ```!==```.  These two operators will compare values without changing types.

The other comparison operators (```==```, ```!=```, ```>```, ...) will coerce types behind the scenes -> ["implicit coercion"](https://github.com/janke-learning/implicit-coercion) <- before making the comparison.  This behavior is important to understand but is far more complicated than the two strict comparison operators.  learn about them some other time

> [NaN is weird.](./nan.md)

### Index
* [strict equality](#strict-equality)
* [strict inequality](#strict-inequality)

---

## Strict Equality


```===```: this operator evaluates to true if the type _and_ value are the same.  

[on pytut](http://www.pythontutor.com/live.html#code=/*%20values%20to%20try%0A%20%20%22%22,%20%22%20%22,%20%0A%20%20true,%20false,%20null,%20undefined,%20%0A%20%200,%200.0,%20-0,%20%2B0,%20-0.0,%20%2B0.0%0A%20%201000,%20.001,%201e3,%201e-3,%20%0A%20%20999e305,%20999e306,%20Infinity%0A%20%20NaN%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20path%20%3D%20%22%22%3B%0Aif%20%28typeof%20a%20%3D%3D%3D%20typeof%20b%29%20%7B%0A%20%20path%20%3D%20%22same%20type%20%26%20value%22%3B%0A%7D%20else%20%7B%0A%20%20path%20%3D%20%22different%20type%20or%20value%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20path,%20%22path%20%3D%3D%3D%20%22%20%2B%20path%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{
  /* values to try
    "", " ", 
    true, false, null, undefined, 
    0, 0.0, -0, +0, -0.0, +0.0
    1000, .001, 1e3, 1e-3, 
    999e305, 999e306, Infinity
    NaN
  */
  const a = , b = ;
  const expected = "";

  let path = "";
  if (typeof a === typeof b) {
    path = "same type & value";
  } else {
    path = "different type or value";
  }

  console.log("a: "+typeof a+", "+a);
  console.log("b: "+typeof b+", "+b);
  console.assert(expected === path, "path === " + path);
}
```

[TOP](#strict-comparisons)

---

## Strict Inequality


```!==```:  This operator evaluates to true if the type _or_ value are not the same.

[on pytut](http://www.pythontutor.com/live.html#code=/*%20values%20to%20try%0A%20%20%22%22,%20%22%20%22,%20%0A%20%20true,%20false,%20null,%20undefined,%20%0A%20%200,%200.0,%20-0,%20%2B0,%20-0.0,%20%2B0.0%0A%20%201000,%20.001,%201e3,%201e-3,%20%0A%20%20999e305,%20999e306,%20Infinity%0A%20%20NaN%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20path%20%3D%20%22%22%3B%0Aif%20%28typeof%20a%20!%3D%3D%20typeof%20b%29%20%7B%0A%20%20path%20%3D%20%22different%20type%22%3B%0A%7D%20else%20%7B%0A%20%20path%20%3D%20%22same%20types%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20path,%20%22path%20%3D%3D%3D%20%22%20%2B%20path%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false) 
```js
{
  /* values to try
    "", " ", 
    true, false, null, undefined, 
    0, 0.0, -0, +0, -0.0, +0.0
    1000, .001, 1e3, 1e-3, 
    999e305, 999e306, Infinity
    NaN
  */
  const a = , b = ;
  const expected = "";

  let path = "";
  if (typeof a !== typeof b) {
    path = "different type or value";
  } else {
    path = "same type & value";
  }

  console.log("a: "+typeof a+", "+a);
  console.log("b: "+typeof b+", "+b);
  console.assert(expected === path, "path === " + path);
}
```


[TOP](#strict-comparisons)

___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>
