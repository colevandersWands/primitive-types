# Primitive Types

Primitives are the types that _are_ values, as opposed to reference types that _contain_ values. (mostly, null is the only exception - it is a primitive with type ```object```).  Primitives are all [stored directly by value](https://github.com/janke-learning/reference-vs-value) and are copied when assigned to other variables.

(this resource ignores Symbol types for now, using them is a bit more complicated than the other primitive types)

### Index
* [the types](#the-types)
* [types and values](#types-and-values)
* [strict comparisons](./strict-comparisons)
* [explicit coercion](./explicit-coercion.md)
* [NaN](./nan.md)
* [null vs. undefined](./null-vs-undefined.md)
* [review script](#review-script)
* [resources](#resources)

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

[on pytut](http://www.pythontutor.com/live.html#code=/*%20values%20to%20try%0A%20%20%22%22,%20%22%20%22,%20true,%20false,%20undefined,%20%0A%20%20null,%20NaN,%20Infinity,%200,%201,%20-1,%20%0A%20%20.5,%20-0.0,%201e3,%201e-3,%20999e305,%20999e306,%0A%20%20%7B%7D,%20%5B%5D,%20function%28%29%7B%7D,%20%28%29%3D%3E%7B%7D,%20new%20Number%28%29%0A*/%0Aconst%20a%20%3D%20%3B%0Aconst%20expected%20%3D%20''%3B%0A%0Alet%20path%20%3D%20%22%22%3B%0Aif%20%28typeof%20a%20%3D%3D%3D%20'string'%29%20%7B%0A%20%20path%20%3D%20typeof%20a%3B%0A%7D%20else%20if%20%28typeof%20a%20%3D%3D%3D%20'number'%29%20%7B%0A%20%20path%20%3D%20typeof%20a%3B%0A%7D%20else%20if%20%28typeof%20a%20%3D%3D%3D%20'boolean'%29%20%7B%0A%20%20path%20%3D%20typeof%20a%3B%0A%7D%20else%20if%20%28typeof%20a%20%3D%3D%3D%20'undefined'%29%20%7B%0A%20%20path%20%3D%20typeof%20a%3B%0A%7D%20else%20if%20%28typeof%20a%20%3D%3D%3D%20'object'%20%26%26%20a%20%3D%3D%3D%20null%29%20%7B%0A%20%20path%20%3D%20typeof%20a%3B%0A%7D%20else%20%7B%0A%20%20path%20%3D%20typeof%20a%20%2B%20%22%3A%20is%20not%20a%20primitive%22%3B%0A%7D%3B%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20type,%20%22typeof%20a%20%3D%3D%3D%20%22%20%2B%20type%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
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

  let path = "";
  if (typeof a === 'string') {
    path = typeof a;
  } else if (typeof a === 'number') {
    path = typeof a;
  } else if (typeof a === 'boolean') {
    path = typeof a;
  } else if (typeof a === 'undefined') {
    path = typeof a;
  } else if (typeof a === 'object' && a === null) {
    path = typeof a;
  } else {
    path = typeof a + ": is not a primitive";
  };

  console.log("a: "+typeof a+", ", a);
  console.assert(expected === path, "typeof a === " + path);
}
```

[TOP](#primitive-types)

---

## Types and Values


Within each type there are different values
* string: anything between ""
* number: anything made up of numbers (num, num.num), Infinity, NaN, with or without ```-/+```, [scientific notation](http://www.java2s.com/Tutorials/Javascript/Javascript_Tutorial/Data_Type/How_to_write_Scientific_notation_literal_in_Javascript.htm)
* boolean: true, false
* undefined: undefined
* null: null 

[on pytut](http://www.pythontutor.com/live.html#code=/*%0A%20%20%22%22,%20%22%20%22,%20%22%20%20%22,%20%22%20%20%22,%20'',%20'%20'%0A%20%20true,%20false,%20null,%20undefined,%20%0A%20%200,%200.0,%20-0,%20%2B0,%20-0.0,%20%2B0.0%0A%20%201000,%20.001,%201e3,%201e-3,%20%0A%20%20999e305,%20999e306,%20Infinity%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20path%20%3D%20%22%22%3B%0Aif%20%28typeof%20a%20%3D%3D%3D%20typeof%20b%29%20%7B%0A%20%20path%20%2B%3D%20%22same%20type,%20%22%3B%0A%20%20if%20%28a%20%3D%3D%3D%20b%20%7C%7C%20%28%20a!%3D%3Da%20%26%26%20b!%3D%3Db%20%29%20%29%20%7B%0A%20%20%20%20path%20%2B%3D%20%22same%20value%22%3B%0A%20%20%7D%20else%20%7B%0A%20%20%20%20path%20%2B%3D%20%22different%20values%22%3B%0A%20%20%7D%0A%7D%20else%20%7B%0A%20%20path%20%3D%20%22different%20types%20%26%20values%22%3B%0A%7D%0A%0Aconsole.log%28%22a%3A%20%22%2Btypeof%20a%2B%22,%20%22%2Ba%29%3B%0Aconsole.log%28%22b%3A%20%22%2Btypeof%20b%2B%22,%20%22%2Bb%29%3B%20%0Aconsole.assert%28expected%20%3D%3D%3D%20path,%20%22path%20%3D%3D%3D%20%22%20%2B%20path%29%3B%0A&cumulative=false&curInstr=27&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
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

  let path = "";
  if (typeof a === typeof b) {
    path += "same type, ";
    if (a === b || ( a!==a && b!==b ) ) {
      path += "same value";
    } else {
      path += "different values";
    }
  } else {
    path = "different types & values";
  }

  console.log("a: "+typeof a+", "+a);
  console.log("b: "+typeof b+", "+b); 
  console.assert(expected === path, "path === " + path);
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
                  {}, [], function(){}, ()=>{}, new Number(),
                  "add values here and guess where they'll fit!"
                ];
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

---

## Resources



___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>

