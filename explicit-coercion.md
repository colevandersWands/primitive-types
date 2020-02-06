# Explicit Coercion


JS allows you to convert between types:
* these rules are learnable, but confusing and not always logical
* simply learn them, do not question them (yet). Someone simply wrote JS to be this way

This repository covers the basic functions for intentionally converting primitives from one type to another.  JavaScript will sometimes change types behind the scenes but that's [a conversation for another day](https://github.com/janke-learning/implicit-coercion).

### Index:
* [to boolean](#to-boolean)
* [to string](#to-string)
* [to number](#to-number)
<!-- * [to undefined](#to-undefined) -->
* (there's no way to convert to ```null```)
* [resources](#resources)

---


### To Boolean

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

  console.log("a: "+typeof a+", "+a);
  console.log("b: "+typeof b+", "+b);
  console.log("a_coerced: "+typeof a_coerced+", "+a_coerced);
  console.log("b_coerced: "+typeof b_coerced+", "+b_coerced);
  console.assert(expected === path, "path === " + path);
}
```

> for more info, see [truthiness](https://github.com/janke-learning/truthiness)

[TOP](#explicit-coercion)

---

## To String

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

  console.log("a: "+typeof a+", "+a);
  console.log("b: "+typeof b+", "+b);
  console.log("a_coerced: "+typeof a_coerced+", "+a_coerced);
  console.log("b_coerced: "+typeof b_coerced+", "+b_coerced);
  console.assert(expected === path, "path === " + path);
}
```

[TOP](#explicit-coercion)

---

## To Number

[on pytut](http://www.pythontutor.com/live.html#code=/*%0A%20%20'1',%20%221.0%22,%20%220%22,%20'0.0',%20'Infinity',%20'NaN',%20'1e3'%0A%20%20'one',%20'two',%20'words',%20'-%3C%28%3D%29%3E-'%0A%20%20true,%20false%0A%20%20undefined,%20null%0A%20%201,%201.0,%200,%200.0,%20-0,%20%2B0,%20Infinity,%20NaN,%201e3,%201000%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20a_coerced%20%3D%20Number%28a%29%3B%0Aconst%20b_coerced%20%3D%20Number%28b%29%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20path%20%3D%20%22%22%3B%0Aif%20%28a_coerced%20%3D%3D%3D%20b_coerced%29%20%7B%0A%20%20path%20%3D%20%22coerce%20to%20same%20number%22%3B%0A%7D%20else%20if%20%28%20%28a_coerced%20!%3D%3D%20a_coerced%29%20%26%26%20%28b_coerced%20!%3D%3D%20b_coerced%29%20%29%20%7B%0A%20%20path%20%3D%20%22both%20coerce%20to%20NaN%22%0A%7D%20else%20%7B%0A%20%20path%20%3D%20%22coerce%20to%20different%20numbers%22%3B%0A%7D%0A%0Aconsole.log%28%22a%3A%20%22%2Btypeof%20a%2B%22,%20%22%2Ba%29%3B%0Aconsole.log%28%22b%3A%20%22%2Btypeof%20b%2B%22,%20%22%2Bb%29%3B%0Aconsole.log%28%22a_coerced%3A%20%22%2Btypeof%20a_coerced%2B%22,%20%22%2Ba_coerced%29%3B%0Aconsole.log%28%22b_coerced%3A%20%22%2Btypeof%20b_coerced%2B%22,%20%22%2Bb_coerced%29%3B%0Aconsole.assert%28expected%20%3D%3D%3D%20path,%20%22path%20%3D%3D%3D%20%22%20%2B%20path%29%3B&cumulative=false&curInstr=27&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{ // coercing to number
  /*
    '1', "1.0", "0", '0.0', 'Infinity', 'NaN', '1e3'
    'one', 'two', 'words', '-<(=)>-'
    true, false
    undefined, null
    1, 1.0, 0, 0.0, -0, +0, Infinity, NaN, 1e3, 1000
  */
  const a = , b = ;
  const a_coerced = Number(a);
  const b_coerced = Number(b);
  const expected = "";

  let path = "";
  if (a_coerced === b_coerced) {
    path = "coerce to same number";
  } else if ( (a_coerced !== a_coerced) && (b_coerced !== b_coerced) ) {
    path = "both coerce to NaN"
  } else {
    path = "coerce to different numbers";
  }

  console.log("a: "+typeof a+", "+a);
  console.log("b: "+typeof b+", "+b);
  console.log("a_coerced: "+typeof a_coerced+", "+a_coerced);
  console.log("b_coerced: "+typeof b_coerced+", "+b_coerced);
  console.assert(expected === path, "path === " + path);
}
```

[TOP](#explicit-coercion)

---
<!--
## To Undefined

[on pytut](http://www.pythontutor.com/live.html#code=/*%20values%20to%20try%0A%20%20try%20everything,%20this%20one's%20not%20to%20complex%0A*/%0Aconst%20a%20%3D%20,%20b%20%3D%20%3B%0Aconst%20a_coerced%20%3D%20void%20a%3B%0Aconst%20b_coerced%20%3D%20void%20b%3B%0Aconst%20expected%20%3D%20%22%22%3B%0A%0Alet%20path%20%3D%20%22%22%3B%0Aif%20%28a_coerced%20%3D%3D%3D%20b_coerced%29%20%7B%0A%20%20path%20%3D%20%22coerce%20to%20same%20undefined%22%3B%0A%7D%20else%20%7B%0A%20%20path%20%3D%20%22coerce%20to%20different%20undefineds%22%3B%0A%7D%0A%0Aconsole.assert%28expected%20%3D%3D%3D%20path,%20%22path%20%3D%3D%3D%20%22%20%2B%20path%29%3B&cumulative=false&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{ // coercing to undefined
  /* values to try
    try everything, this one's not to complicated
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

  console.log("a: "+typeof a+", "+a);
  console.log("b: "+typeof b+", "+b);
  console.log("a_coerced: "+typeof a_coerced+", "+a_coerced);
  console.log("b_coerced: "+typeof b_coerced+", "+b_coerced);
  console.assert(expected === path, "path === " + path);
}
```


[TOP](#explicit-coercion)

---
-->

## Resources

* [data types](https://javascript.info/types)
* [type conversions](https://javascript.info/type-conversions)

___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>

