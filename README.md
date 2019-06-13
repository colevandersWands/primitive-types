# Primitive Types

Primitives are the types of value that _are_ values, as opposed to reference types that _contain_ values. (mostly, null is the only exception).  Primitives are all stored directly by variables and are copied when assigned to other variables.

(this resource ignores Symbol types for now, using them is a bit more complicated than the other primitive types)

### Index
* [the types](#the-types)
* [=== & !==](#equal-and-not-equal)
* [NaN](#nan)
* [null vs. undefined](#null-vs-undefined)
* [type and value](#type-and-value)
* coercing to
    * [boolean](#boolean)
    * [string](#string)
    * [number](#number)
    * [undefined](#undefined)
* [review script](#review-script)

---

## The Types

there are 5 primitive types
* string
* number
* boolean
* undefined
* null
* (we'll ignore Symbol for now)

the typeof operator tells what type a thing is
* typeof (anything in quotes) === "string"
* typeof (NaN, Infinity, numbers) === "number"
* typeof (true or false) === "boolean"
* typeof undefined === undefined
* typeof null === null

[on pytut](http://www.pythontutor.com/live.html#code=/*%20values%20to%20try%0A%20%20%22%22,%20%22%20%22,%20true,%20false,%20undefined,%20%0A%20%20null,%20NaN,%20Infinity,%200,%201,%20-1,%20%0A%20%20.5,%20-0.0,%201e3,%201e-3,%20999e305,%20999e306,%0A%20%20%7B%7D,%20%5B%5D,%20function%28%29%7B%7D,%20%28%29%3D%3E%7B%7D,%20new%20Number%28%29%0A*/%0Aconst%20a%20%3D%20%3B%0Aconst%20expected%20%3D%20''%3B%0A%0Alet%20actual%20%3D%20%22%22%3B%0Aif%20%28typeof%20a%20%3D%3D%3D%20'string'%29%20%7B%0A%20%20actual%20%3D%20typeof%20a%3B%0A%7D%20else%20if%20%28typeof%20a%20%3D%3D%3D%20'number'%29%20%7B%0A%20%20actual%20%3D%20typeof%20a%3B%0A%7D%20else%20if%20%28typeof%20a%20%3D%3D%3D%20'boolean'%29%20%7B%0A%20%20actual%20%3D%20typeof%20a%3B%0A%7D%20else%20if%20%28typeof%20a%20%3D%3D%3D%20'undefined'%29%20%7B%0A%20%20actual%20%3D%20typeof%20a%3B%0A%7D%20else%20if%20%28typeof%20a%20%3D%3D%3D%20'object'%20%26%26%20a%20%3D%3D%3D%20null%29%20%7B%0A%20%20actual%20%3D%20typeof%20a%3B%0A%7D%20else%20%7B%0A%20%20actual%20%3D%20typeof%20a%20%2B%20%22%3A%20is%20not%20a%20primitive%22%3B%0A%7D%3B%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20type,%20%22typeof%20a%20%3D%3D%3D%20%22%20%2B%20type%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{
  /* values to try
    "", " ", true, false, undefined, 
    null, NaN, Infinity, 0, 1, -1, 
    .5, -0.0, 1e3, 1e-3, 999e305, 999e306,
    {}, [], function(){}, ()=>{}, new Number()
  */
  const a = ;
  const expected = '';

  let actual = "";
  if (typeof a === 'string') {
    actual = typeof a;
  } else if (typeof a === 'number') {
    actual = typeof a;
  } else if (typeof a === 'boolean') {
    actual = typeof a;
  } else if (typeof a === 'undefined') {
    actual = typeof a;
  } else if (typeof a === 'object' && a === null) {
    actual = typeof a;
  } else {
    actual = typeof a + ": is not a primitive";
  };

  console.assert(expected === type, "typeof a === " + type);
}
```

[TOP](#primitive-types)

---

## Equal and Not Equal


__===__: this operator evaluates to true if the type _and_ value are the same.  

[on pytut](http://www.pythontutor.com/live.html#code=/*%20values%20to%20try%0A%20%20%22%22,%20%22%20%22,%20%0A%20%20true,%20false,%20null,%20undefined,%20%0A%20%200,%200.0,%20-0,%20%2B0,%20-0.0,%20%2B0.0%0A%20%201000,%20.001,%201e3,%201e-3,%20%0A%20%20999e305,%20999e306,%20Infinity%0A%20%20NaN%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20actual%20%3D%20%22%22%3B%0Aif%20%28typeof%20a%20%3D%3D%3D%20typeof%20b%29%20%7B%0A%20%20actual%20%3D%20%22same%20type%22%3B%0A%7D%20else%20%7B%0A%20%20actual%20%3D%20%22different%20types%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20actual,%20%22actual%20%3D%3D%3D%20%22%20%2B%20actual%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
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

  let actual = "";
  if (typeof a === typeof b) {
    actual = "same type";
  } else {
    actual = "different types";
  }

  console.assert(expected === actual, "actual === " + actual);
}
```



```__!==__```:  This operator evaluates to true if the type _or_ value are not the same.

[on pytut](http://www.pythontutor.com/live.html#code=/*%20values%20to%20try%0A%20%20%22%22,%20%22%20%22,%20%0A%20%20true,%20false,%20null,%20undefined,%20%0A%20%200,%200.0,%20-0,%20%2B0,%20-0.0,%20%2B0.0%0A%20%201000,%20.001,%201e3,%201e-3,%20%0A%20%20999e305,%20999e306,%20Infinity%0A%20%20NaN%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20actual%20%3D%20%22%22%3B%0Aif%20%28typeof%20a%20!%3D%3D%20typeof%20b%29%20%7B%0A%20%20actual%20%3D%20%22different%20type%22%3B%0A%7D%20else%20%7B%0A%20%20actual%20%3D%20%22same%20types%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20actual,%20%22actual%20%3D%3D%3D%20%22%20%2B%20actual%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false) 
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

  let actual = "";
  if (typeof a !== typeof b) {
    actual = "different type";
  } else {
    actual = "same types";
  }

  console.assert(expected === actual, "actual === " + actual);
}
```


[TOP](#primitive-types)

---

## NaN

careful of NaN, it's strange.  The best way to check if something is NaN is to use isNaN(_);

[on pytut](http://www.pythontutor.com/live.html#code=/*%0A%20%20NaN%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20expected%20%3D%20%3B%0A%0Alet%20result%3B%0Aif%20%28a%20%3D%3D%3D%20b%29%20%7B%0A%20%20result%20%3D%20'the%20same%20not-NaNs'%3B%0A%7D%20else%20if%20%28%20isNaN%28a%29%20%3D%3D%3D%20isNaN%28b%29%20%29%20%7B%0A%20%20result%20%3D%20'both%20NaN'%3B%0A%7D%20else%20%7B%0A%20%20result%20%3D%20'not%20the%20same'%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20result%29&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{
  /*
    NaN
  */
  const a = , b = ;
  const expected = ;

  let result;
  if (a === b) {
    result = 'the same not-NaNs';
  } else if ( isNaN(a) === isNaN(b) ) {
    result = 'both NaN';
  } else {
    result = 'not the same'
  }

  console.assert(expected === result)
}
```


[TOP](#primitive-types)

---

## Null vs Undefined


null vs. undefined  
* null is intentional
* undefined can happen by accident

so use null if you want there to be nothing, and undefined if there isn't a value yet

[on pytut](http://www.pythontutor.com/live.html#code=const%20typeof_undefined%20%3D%20typeof%20undefined%3B%0Aconst%20typeof_null%20%3D%20typeof%20null%3B%0A%0Aconst%20both_falsey%20%3D%20Boolean%28null%29%20%3D%3D%3D%20Boolean%28undefined%29%3B%0A%0Aconst%20unassigned_variable%3B%20//%20undefined%20by%20default%0Aconst%20assigned_undefined%20%3D%20undefined%3B%0Aconst%20assigned_null%20%3D%20null%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{
  const typeof_undefined = typeof undefined;
  const typeof_null = typeof null;

  const both_falsey = Boolean(null) === Boolean(undefined);

  const unassigned_variable; // undefined by default
  const assigned_undefined = undefined;
  const assigned_null = null;
}
```

[TOP](#primitive-types)

---

## Types and Values


in each type there are different values
* string: anything between ""
* number: anything made up of numbers *.*, Infinity, NaN, with or without -
* boolean: true, false
* undefined: undefined
* null: null 

[on pytut](http://www.pythontutor.com/live.html#code=/*%0A%20%20%22%22,%20%22%20%22,%20%22%20%20%22,%20%22%20%20%22,%20'',%20'%20'%0A%20%20true,%20false,%20null,%20undefined,%20%0A%20%200,%200.0,%20-0,%20%2B0,%20-0.0,%20%2B0.0%0A%20%201000,%20.001,%201e3,%201e-3,%20%0A%20%20999e305,%20999e306,%20Infinity%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20actual%20%3D%20%22%22%3B%0Aif%20%28typeof%20a%20%3D%3D%3D%20typeof%20b%29%20%7B%0A%20%20actual%20%2B%3D%20%22same%20type,%20%22%3B%0A%20%20if%20%28a%20%3D%3D%3D%20b%29%20%7B%0A%20%20%20%20actual%20%2B%3D%20%22same%20value%22%3B%0A%20%20%7D%20else%20%7B%0A%20%20%20%20actual%20%2B%3D%20%22different%20values%22%3B%0A%20%20%7D%0A%7D%20else%20%7B%0A%20%20actual%20%3D%20%22different%20types%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20actual,%20%22actual%20%3D%3D%3D%20%22%20%2B%20actual%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{
  /*
    "", " ", "  ", "  ", '', ' '
    true, false, null, undefined, 
    0, 0.0, -0, +0, -0.0, +0.0
    1000, .001, 1e3, 1e-3, 
    999e305, 999e306, Infinity
  */
  const a = , b = ;
  const expected = "";

  let actual = "";
  if (typeof a === typeof b) {
    actual += "same type, ";
    if (a === b) {
      actual += "same value";
    } else {
      actual += "different values";
    }
  } else {
    actual = "different types";
  }

  console.assert(expected === actual, "actual === " + actual);
}
```

[TOP](#primitive-types)

---

## Coercing To


JS allows you to convert between types
* these rules are understandable, but confusing
* simply learn them, do not question them (yet). Someone simply wrote JS to be this way
* Boolean(x) -> turns x into a boolean
* String(x) -> turns x into a string
* Number(x) -> turns x into a number
* void(x) -> turns x into undefined
* (no way to convert to null)




### Boolean

[on pytut](http://www.pythontutor.com/live.html#code=/*%20%20values%20to%20try%0A%20%20%22%22,%20%22%20%22,%20true,%20false,%20undefined,%20null,%200,%201,%20-1,%20NaN,%20Infinity%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20a_coerced%20%3D%20Boolean%28a%29%3B%0Aconst%20b_coerced%20%3D%20Boolean%28b%29%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20actual%20%3D%20%22%22%3B%0Aif%20%28a_coerced%20%3D%3D%3D%20b_coerced%29%20%7B%0A%20%20actual%20%3D%20%22coerce%20to%20same%20boolean%22%3B%0A%7D%20else%20%7B%0A%20%20actual%20%3D%20%22coerce%20to%20different%20booleans%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20actual,%20%22actual%20%3D%3D%3D%20%22%20%2B%20actual%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{ // coercing to boolean
  /*  values to try
    "", " ", true, false, undefined, null, 0, 1, -1, NaN, Infinity
  */
  const a = , b = ;
  const a_coerced = Boolean(a);
  const b_coerced = Boolean(b);
  const expected = "";

  let actual = "";
  if (a_coerced === b_coerced) {
    actual = "coerce to same boolean";
  } else {
    actual = "coerce to different booleans";
  }

  console.assert(expected === actual, "actual === " + actual);
}
```

### String

[on pytut](http://www.pythontutor.com/live.html#code=/*%0A%20%20%22%22,%20%22%20%22,%20true,%20false,%20undefined,%20null,%200,%201,%20-1,%20NaN,%20Infinity%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20a_coerced%20%3D%20String%28a%29%3B%0Aconst%20b_coerced%20%3D%20String%28b%29%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20actual%20%3D%20%22%22%3B%0Aif%20%28a_coerced%20%3D%3D%3D%20b_coerced%29%20%7B%0A%20%20actual%20%3D%20%22coerce%20to%20same%20string%22%3B%0A%7D%20else%20%7B%0A%20%20actual%20%3D%20%22coerce%20to%20different%20strings%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20actual,%20%22actual%20%3D%3D%3D%20%22%20%2B%20actual%29%3B%0A&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{ // coercing to string
  /*
    "", " ", true, false, undefined, null, 0, 1, -1, NaN, Infinity
  */
  const a = , b = ;
  const a_coerced = String(a);
  const b_coerced = String(b);
  const expected = "";

  let actual = "";
  if (a_coerced === b_coerced) {
    actual = "coerce to same string";
  } else {
    actual = "coerce to different strings";
  }

  console.assert(expected === actual, "actual === " + actual);
}
```

### Number

[on pytut](http://www.pythontutor.com/live.html#code=/*%0A%20%20'1',%20%221.0%22,%20%220%22,%20'0.0',%20'Infinity',%20'NaN',%20'1e3'%0A%20%20'one',%20'two',%20'words',%20'-%3C%28%3D%29%3E-'%0A%20%20true,%20false%0A%20%20undefined,%20null%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20a_coerced%20%3D%20Number%28a%29%3B%0Aconst%20b_coerced%20%3D%20Number%28b%29%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20actual%20%3D%20%22%22%3B%0Aif%20%28a_coerced%20%3D%3D%3D%20b_coerced%29%20%7B%0A%20%20actual%20%3D%20%22coerce%20to%20same%20number%22%3B%0A%7D%20else%20%7B%0A%20%20actual%20%3D%20%22coerce%20to%20different%20numbers%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20actual,%20%22actual%20%3D%3D%3D%20%22%20%2B%20actual%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{ // coercing to number
  /*
    '1', "1.0", "0", '0.0', 'Infinity', 'NaN', '1e3'
    'one', 'two', 'words', '-<(=)>-'
    true, false
    undefined, null
  */
  const a = , b = ;
  const a_coerced = Number(a);
  const b_coerced = Number(b);
  const expected = "";

  let actual = "";
  if (a_coerced === b_coerced) {
    actual = "coerce to same number";
  } else {
    actual = "coerce to different numbers";
  }

  console.assert(expected === actual, "actual === " + actual);
}
```

### Undefined

[on pytut](http://www.pythontutor.com/live.html#code=/*%20values%20to%20try%0A%20%20try%20everything,%20this%20one's%20not%20to%20complex%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20a_coerced%20%3D%20void%20a%3B%0Aconst%20b_coerced%20%3D%20void%20b%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20actual%20%3D%20%22%22%3B%0Aif%20%28a_coerced%20%3D%3D%3D%20b_coerced%29%20%7B%0A%20%20actual%20%3D%20%22coerce%20to%20same%20undefined%22%3B%0A%7D%20else%20%7B%0A%20%20actual%20%3D%20%22coerce%20to%20different%20undefineds%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20actual,%20%22actual%20%3D%3D%3D%20%22%20%2B%20actual%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{ // coercing to undefined
  /* values to try
    try everything, this one's not to complex
  */
  const a = , b = ;
  const a_coerced = void a;
  const b_coerced = void b;
  const expected = "";

  let actual = "";
  if (a_coerced === b_coerced) {
    actual = "coerce to same undefined";
  } else {
    actual = "coerce to different undefineds";
  }

  console.assert(expected === actual, "actual === " + actual);
}
```

[TOP](#primitive-types)

---

## Review Script

[on pytut](http://www.pythontutor.com/live.html#code=const%20things%20%3D%20%5B%22%22,%20%22%20%22,%20true,%20false,%20undefined,%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20null,%20NaN,%20Infinity,%200,%201,%20-1,%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20.5,%20-0.0,%201e3,%201e-3,%20999e305,%20999e306,%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D,%20%5B%5D,%20function%28%29%7B%7D,%20%28%29%3D%3E%7B%7D,%20new%20Number%28%29%5D%3B%0Aconst%20sorted%20%3D%20%7B%0A%20%20%20%20string%3A%20%5B%5D,%0A%20%20%20%20number%3A%20%5B%5D,%0A%20%20%20%20boolean%3A%20%5B%5D,%0A%20%20%20%20null%3A%20%5B%5D,%0A%20%20%20%20undefined%3A%20%5B%5D,%0A%20%20%20%20not_a_primitive%3A%20%5B%5D%0A%20%20%7D%3B%20%0A%0Afor%20%28let%20thing%20of%20things%29%20%7B%0A%20%20if%20%28typeof%20thing%20%3D%3D%3D%20'object'%20%26%26%20thing%20%3D%3D%3D%20null%29%20%7B%0A%20%20%20%20sorted.null.push%28thing%29%3B%0A%20%20%7D%20else%20if%20%28typeof%20thing%20%3D%3D%3D%20'object'%29%20%7B%0A%20%20%20%20sorted.not_a_primitive.push%28thing%29%3B%0A%20%20%7D%20else%20if%20%28typeof%20thing%20%3D%3D%3D%20'function'%29%20%7B%0A%20%20%20%20sorted.not_a_primitive.push%28thing%29%3B%0A%20%20%7D%20else%20%7B%0A%20%20%20%20sorted%5Btypeof%20thing%5D.push%28thing%29%3B%0A%20%20%7D%0A%7D%0A%0Aconsole.log%28sorted%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{
  const things = ["", " ", true, false, undefined, 
                  null, NaN, Infinity, 0, 1, -1, 
                  .5, -0.0, 1e3, 1e-3, 999e305, 999e306,
                  {}, [], function(){}, ()=>{}, new Number()];
  const sorted = {
      string: [],
      number: [],
      boolean: [],
      null: [],
      undefined: [],
      not_a_primitive: []
    }; 

  for (let thing of things) {
    if (typeof thing === 'object' && thing === null) {
      sorted.null.push(thing);
    } else if (typeof thing === 'object') {
      sorted.not_a_primitive.push(thing);
    } else if (typeof thing === 'function') {
      sorted.not_a_primitive.push(thing);
    } else {
      sorted[typeof thing].push(thing);
    }
  }

  console.log(sorted);
}
```




___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>

