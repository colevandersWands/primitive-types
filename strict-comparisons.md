## Strict Comparisons

There are two strict comparison operators, ```===``` and ```!==```.  These two operators will compare values without changing types.

The other comparison operators (```==```, ```!=```, ```>```, ...) will coerce types behind the scenes -> ["implicit coercion"](https://github.com/janke-learning/implicit-coercion) <- before making the comparison.  This behavior is important to understand but is far more complicated than the two strict comparison operators.  learn about them some other time

> [NaN is weird.](./nan.md)

### Index
* [strict equality](#strict-equality)
* [strict inequality](#strict-inequality)

---

## Strict Equality


```===```: this operator evaluates to true if the type _and_ value are the same. (exept NaN, two NaN's returns false)

[on pytut](http://www.pythontutor.com/live.html#code=/*%20values%20to%20try%0A%20%20%22%22,%20%22%20%22,%20%22%20%20%22,%20%60%20%20%60,%20'',%20'%20'%0A%20%20true,%20false,%20null,%20undefined,%20%0A%20%200,%200.0,%20-0,%20%2B0,%20-0.0,%20%2B0.0%0A%20%201000,%20.001,%201e3,%201e-3,%20%0A%20%20999e305,%20999e306,%20Infinity%0A%20%20%223%22,%203,%20%22true%22,%20true,%0A%20%20NaN,%20%22NaN%22,%201,%203/3%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0A%0Aconst%20strictly_equal%20%3D%20a%20%3D%3D%3D%20b%3B%0A%0Alet%20compared%20%3D%20%22%22%3B%0Aif%20%28strictly_equal%29%20%7B%0A%20%20compared%20%3D%20%22same%20type%20%26%20value%22%3B%0A%7D%20else%20%7B%0A%20%20compared%20%3D%20%22different%20type%20and/or%20value%20%28or%20both%20NaN%29%22%3B%0A%7D&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{
  /* values to try
    "", " ", "  ", `  `, '', ' '
    true, false, null, undefined, 
    0, 0.0, -0, +0, -0.0, +0.0
    1000, .001, 1e3, 1e-3, 
    999e305, 999e306, Infinity
    "3", 3, "true", true,
    NaN, "NaN", 1, 3/3
  */
  const a = , b = ;

  const strictly_equal = a === b;
  
  let compared = "";
  if (strictly_equal) {
    compared = "same type & value";
  } else {
    compared = "different type and/or value (or both NaN)";
  }
  
  console.log("a: "+typeof a+", "+a);
  console.log("b: "+typeof b+", "+b);
  console.log("strictly_equal: "+typeof strictly_equal+", "+strictly_equal);
  console.log("compared: "+compared);
}
```

[TOP](#strict-comparisons)

---

## Strict Inequality


```!==```:  This operator evaluates to true if the type _or_ value are not the same. (or if both are NaN)

[on pytut](http://www.pythontutor.com/live.html#code=/*%20values%20to%20try%0A%20%20%22%22,%20%22%20%22,%20%22%20%20%22,%20%60%20%20%60,%20'',%20'%20'%0A%20%20true,%20false,%20null,%20undefined,%20%0A%20%200,%200.0,%20-0,%20%2B0,%20-0.0,%20%2B0.0%0A%20%201000,%20.001,%201e3,%201e-3,%20%0A%20%20999e305,%20999e306,%20Infinity%0A%20%20%223%22,%203,%20%22true%22,%20true,%0A%20%20NaN,%20%22NaN%22,%201,%203/3%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0A%0Aconst%20strictly_inequal%20%3D%20a%20!%3D%3D%20b%3B%0A%0Alet%20compared%20%3D%20%22%22%3B%0Aif%20%28strictly_inequal%29%20%7B%0A%20%20compared%20%3D%20%22different%20type%20and/or%20value%20%28or%20both%20NaN%29%22%3B%0A%7D%20else%20%7B%0A%20%20compared%20%3D%20%22same%20type%20and%20value%22%3B%0A%7D&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false) 
```js
{
  /* values to try
    "", " ", "  ", `  `, '', ' '
    true, false, null, undefined, 
    0, 0.0, -0, +0, -0.0, +0.0
    1000, .001, 1e3, 1e-3, 
    999e305, 999e306, Infinity
    "3", 3, "true", true,
    NaN, "NaN", 1, 3/3
  */
  const a = , b = ;

  const strictly_inequal = a !== b;
  
  let compared = "";
  if (strictly_inequal) {
    compared = "different type and/or value (or both NaN)";
  } else {
    compared = "same type and value";
  }
  
  console.log("a: "+typeof a+", "+a);
  console.log("b: "+typeof b+", "+b);
  console.log("strictly_inequal: "+typeof strictly_inequal+", "+strictly_inequal);
  console.log("compared: "+compared);
}
```


[TOP](#strict-comparisons)

___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>
