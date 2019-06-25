# Primitive Types

Primitives are the types that _are_ values, as opposed to reference types that _contain_ values. (mostly, null is the only exception - it is a primitive with type ```object```).  Primitives are all [stored directly by value](https://github.com/janke-learning/reference-vs-value) and are copied when assigned to other variables.

(this resource ignores Symbol types for now, using them is a bit more complicated than the other primitive types)

### Index
* [the types](#the-types)
* [types and values](#types-and-values)
* [=== & !==](#equal-and-not-equal)
* [NaN](#nan)
* [null vs. undefined](#null-vs-undefined)
* coercing to
    * [boolean](#boolean)
    * [string](#string)
    * [number](#number)
    * [undefined](#undefined)
    * (no way to coerce to ```null```)
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

  console.log("a: "+typeof a+", "+a);
  console.assert(expected === type, "typeof a === " + type);
}
```


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

[TOP](#primitive-types)

---

## Equal and Not Equal


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



```__!==__```:  This operator evaluates to true if the type _or_ value are not the same.

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


[TOP](#primitive-types)

---

## NaN

careful of NaN, it's strange.  The best way to check if something is NaN is to compare it to itself (```x !== x```), NaN is the only value that will fail this comparison;

__Just NaN__

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

__NaN and Other Values__

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

__isNaN() & Number.isNaN()__

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


[TOP](#primitive-types)

---

## Null vs Undefined


null vs. undefined  
* ```undefined``` can happen by accident (undefined variable, accessing values that don't exist in data structures, functions without return statements, ```void x```, ...)
* ```null``` is used to show that something is supposed to be empty, JS doesn't create ```null``` behind the scenes (with some little exceptions in the DOM you don't need to worry about yet)

So a general rule: _use ```null```, when you intentionally want something to be empty. this will help other developers and  make it easier to debug your code_

[on pytut](http://www.pythontutor.com/live.html#code=const%20x%20%3D%20null%3B%0Aconsole.log%28%22x%3A%20%22%2B%20typeof%20x%20%2B%22,%20%22%2B%20x%20%2B%22,%20%22%2B%20Boolean%28x%29%20%2B%22y%22%29%3B%0A%0Aconst%20a%20%3D%20undefined%3B%0Aconsole.log%28%22a%3A%20%22%2B%20typeof%20a%20%2B%22,%20%22%2B%20a%20%2B%22,%20%22%2B%20Boolean%28a%29%20%2B%22y%22%29%3B%0A%0Alet%20b%3B%0Aconsole.log%28%22b%3A%20%22%2B%20typeof%20b%20%2B%22,%20%22%2B%20b%20%2B%22,%20%22%2B%20Boolean%28b%29%20%2B%22y%22%29%3B%0A%0Avar%20c%3B%0Aconsole.log%28%22c%3A%20%22%2B%20typeof%20c%20%2B%22,%20%22%2B%20c%20%2B%22,%20%22%2B%20Boolean%28c%29%20%2B%22y%22%29%3B%0A%0Afunction%20func_no_return%28%29%7B%7D%0Aconst%20d%20%3D%20func_no_return%28%29%3B%0Aconsole.log%28%22d%3A%20%22%2B%20typeof%20d%20%2B%22,%20%22%2B%20d%20%2B%22,%20%22%2B%20Boolean%28d%29%20%2B%22y%22%29%3B%0A%0Aconst%20arrow_no_return%20%3D%20%28%29%20%3D%3E%20%7B%7D%3B%0Aconst%20e%20%3D%20arrow_no_return%28%29%3B%0Aconsole.log%28%22e%3A%20%22%2B%20typeof%20e%20%2B%22,%20%22%2B%20e%20%2B%22,%20%22%2B%20Boolean%28e%29%20%2B%22y%22%29%3B%0A%0Aconst%20f%20%3D%20void%20a%3B%0Aconsole.log%28%22f%3A%20%22%2B%20typeof%20f%20%2B%22,%20%22%2B%20f%20%2B%22,%20%22%2B%20Boolean%28f%29%20%2B%22y%22%29%3B%0A%20%20%0Aconst%20obj%20%3D%20%7Bprop%3A%20undefined%7D%3B%0Aconst%20g%20%3D%20obj.prop%3B%0Aconst%20h%20%3D%20obj.does_not_exist%3B%0Aconsole.log%28%22g%3A%20%22%2B%20typeof%20g%20%2B%22,%20%22%2B%20g%20%2B%22,%20%22%2B%20Boolean%28g%29%20%2B%22y%22%29%3B%0Aconsole.log%28%22h%3A%20%22%2B%20typeof%20h%20%2B%22,%20%22%2B%20h%20%2B%22,%20%22%2B%20Boolean%28h%29%20%2B%22y%22%29%3B%0A%0Aconst%20arr%20%3D%20%5Bundefined%5D%3B%0Aconst%20i%20%3D%20arr%5B0%5D%3B%0Aconst%20j%20%3D%20arr%5B1%5D%3B%0Aconsole.log%28%22i%3A%20%22%2B%20typeof%20i%20%2B%22,%20%22%2B%20i%20%2B%22,%20%22%2B%20Boolean%28i%29%20%2B%22y%22%29%3B%0Aconsole.log%28%22j%3A%20%22%2B%20typeof%20j%20%2B%22,%20%22%2B%20j%20%2B%22,%20%22%2B%20Boolean%28j%29%20%2B%22y%22%29%3B%0A&cumulative=false&curInstr=27&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{
  const x = null;
  console.log("x: "+ typeof x +", "+ x +", "+ Boolean(x) +"y");

  const a = undefined;
  console.log("a: "+ typeof a +", "+ a +", "+ Boolean(a) +"y");
  
  let b;
  console.log("b: "+ typeof b +", "+ b +", "+ Boolean(b) +"y");

  var c;
  console.log("c: "+ typeof c +", "+ c +", "+ Boolean(c) +"y");

  function func_no_return(){}
  const d = func_no_return();
  console.log("d: "+ typeof d +", "+ d +", "+ Boolean(d) +"y");
  
  const arrow_no_return = () => {};
  const e = arrow_no_return();
  console.log("e: "+ typeof e +", "+ e +", "+ Boolean(e) +"y");
  
  const f = void a;
  console.log("f: "+ typeof f +", "+ f +", "+ Boolean(f) +"y");
    
  const obj = {prop: undefined};
  const g = obj.prop;
  const h = obj.does_not_exist;
  console.log("g: "+ typeof g +", "+ g +", "+ Boolean(g) +"y");
  console.log("h: "+ typeof h +", "+ h +", "+ Boolean(h) +"y");

  const arr = [undefined];
  const i = arr[0];
  const j = arr[1];
  console.log("i: "+ typeof i +", "+ i +", "+ Boolean(i) +"y");
  console.log("j: "+ typeof j +", "+ j +", "+ Boolean(j) +"y");
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

[on pytut](http://www.pythontutor.com/live.html#code=/*%20%20values%20to%20try%0A%20%20%22%22,%20%22%20%22,%20true,%20false,%20undefined,%20null,%200,%201,%20-1,%20NaN,%20Infinity%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20a_coerced%20%3D%20Boolean%28a%29%3B%0Aconst%20b_coerced%20%3D%20Boolean%28b%29%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20path%20%3D%20%22%22%3B%0Aif%20%28a_coerced%20%3D%3D%3D%20b_coerced%29%20%7B%0A%20%20path%20%3D%20%22coerce%20to%20same%20boolean%22%3B%0A%7D%20else%20%7B%0A%20%20path%20%3D%20%22coerce%20to%20different%20booleans%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20path,%20%22path%20%3D%3D%3D%20%22%20%2B%20path%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{ // coercing to boolean
  /*  values to try
    "", " ", true, false, undefined, null, 0, 1, -1, NaN, Infinity
  */
  const a = , b = ;
  const a_coerced = Boolean(a);
  const b_coerced = Boolean(b);
  const expected = "";

  let path = "";
  if (a_coerced === b_coerced) {
    path = "coerce to same boolean";
  } else {
    path = "coerce to different booleans";
  }

  console.assert(expected === path, "path === " + path);
}
```

### String

[on pytut](http://www.pythontutor.com/live.html#code=/*%0A%20%20%22%22,%20%22%20%22,%20true,%20false,%20undefined,%20null,%200,%201,%20-1,%20NaN,%20Infinity%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20a_coerced%20%3D%20String%28a%29%3B%0Aconst%20b_coerced%20%3D%20String%28b%29%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20path%20%3D%20%22%22%3B%0Aif%20%28a_coerced%20%3D%3D%3D%20b_coerced%29%20%7B%0A%20%20path%20%3D%20%22coerce%20to%20same%20string%22%3B%0A%7D%20else%20%7B%0A%20%20path%20%3D%20%22coerce%20to%20different%20strings%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20path,%20%22path%20%3D%3D%3D%20%22%20%2B%20path%29%3B%0A&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{ // coercing to string
  /*
    "", " ", true, false, undefined, null, 0, 1, -1, NaN, Infinity
  */
  const a = , b = ;
  const a_coerced = String(a);
  const b_coerced = String(b);
  const expected = "";

  let path = "";
  if (a_coerced === b_coerced) {
    path = "coerce to same string";
  } else {
    path = "coerce to different strings";
  }

  console.assert(expected === path, "path === " + path);
}
```

### Number

[on pytut](http://www.pythontutor.com/live.html#code=/*%0A%20%20'1',%20%221.0%22,%20%220%22,%20'0.0',%20'Infinity',%20'NaN',%20'1e3'%0A%20%20'one',%20'two',%20'words',%20'-%3C%28%3D%29%3E-'%0A%20%20true,%20false%0A%20%20undefined,%20null%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20a_coerced%20%3D%20Number%28a%29%3B%0Aconst%20b_coerced%20%3D%20Number%28b%29%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20path%20%3D%20%22%22%3B%0Aif%20%28a_coerced%20%3D%3D%3D%20b_coerced%29%20%7B%0A%20%20path%20%3D%20%22coerce%20to%20same%20number%22%3B%0A%7D%20else%20%7B%0A%20%20path%20%3D%20%22coerce%20to%20different%20numbers%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20path,%20%22path%20%3D%3D%3D%20%22%20%2B%20path%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
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

  let path = "";
  if (a_coerced === b_coerced) {
    path = "coerce to same number";
  } else {
    path = "coerce to different numbers";
  }

  console.assert(expected === path, "path === " + path);
}
```

### Undefined

[on pytut](http://www.pythontutor.com/live.html#code=/*%20values%20to%20try%0A%20%20try%20everything,%20this%20one's%20not%20to%20complex%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20a_coerced%20%3D%20void%20a%3B%0Aconst%20b_coerced%20%3D%20void%20b%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20path%20%3D%20%22%22%3B%0Aif%20%28a_coerced%20%3D%3D%3D%20b_coerced%29%20%7B%0A%20%20path%20%3D%20%22coerce%20to%20same%20undefined%22%3B%0A%7D%20else%20%7B%0A%20%20path%20%3D%20%22coerce%20to%20different%20undefineds%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20path,%20%22path%20%3D%3D%3D%20%22%20%2B%20path%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{ // coercing to undefined
  /* values to try
    try everything, this one's not to complex
  */
  const a = , b = ;
  const a_coerced = void a;
  const b_coerced = void b;
  const expected = "";

  let path = "";
  if (a_coerced === b_coerced) {
    path = "coerce to same undefined";
  } else {
    path = "coerce to different undefineds";
  }

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
                  "add more values and guess where they fit!"
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




___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>

