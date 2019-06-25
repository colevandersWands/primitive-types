# Null vs Undefined


null vs. undefined  
* ```undefined``` can happen by accident (undefined variable, accessing values that don't exist in data structures, functions without return statements, ```void x```, ...)
* ```null``` is used to show that something is supposed to be empty, JS doesn't create ```null``` behind the scenes (with some little exceptions in the DOM you don't need to worry about yet)

So a general rule: _use ```null```, when you intentionally want something to be empty. this will help other developers and  make it easier to debug your code_

[on pytut](http://www.pythontutor.com/live.html#code=const%20x%20%3D%20null%3B%0Aconsole.log%28%22x%3A%20%22%2B%20typeof%20x%20%2B%22,%20%22%2B%20x%20%2B%22,%20%22%2B%20Boolean%28x%29%20%2B%22y%22%29%3B%0A%0Aconst%20a%20%3D%20undefined%3B%0Aconsole.log%28%22a%3A%20%22%2B%20typeof%20a%20%2B%22,%20%22%2B%20a%20%2B%22,%20%22%2B%20Boolean%28a%29%20%2B%22y%22%29%3B%0A%0Alet%20b%3B%0Aconsole.log%28%22b%3A%20%22%2B%20typeof%20b%20%2B%22,%20%22%2B%20b%20%2B%22,%20%22%2B%20Boolean%28b%29%20%2B%22y%22%29%3B%0A%0Avar%20c%3B%0Aconsole.log%28%22c%3A%20%22%2B%20typeof%20c%20%2B%22,%20%22%2B%20c%20%2B%22,%20%22%2B%20Boolean%28c%29%20%2B%22y%22%29%3B%0A%0Afunction%20func_no_return%28%29%7B%7D%0Aconst%20d%20%3D%20func_no_return%28%29%3B%0Aconsole.log%28%22d%3A%20%22%2B%20typeof%20d%20%2B%22,%20%22%2B%20d%20%2B%22,%20%22%2B%20Boolean%28d%29%20%2B%22y%22%29%3B%0A%0Aconst%20arrow_no_return%20%3D%20%28%29%20%3D%3E%20%7B%7D%3B%0Aconst%20e%20%3D%20arrow_no_return%28%29%3B%0Aconsole.log%28%22e%3A%20%22%2B%20typeof%20e%20%2B%22,%20%22%2B%20e%20%2B%22,%20%22%2B%20Boolean%28e%29%20%2B%22y%22%29%3B%0A%0Aconst%20f%20%3D%20void%20a%3B%0Aconsole.log%28%22f%3A%20%22%2B%20typeof%20f%20%2B%22,%20%22%2B%20f%20%2B%22,%20%22%2B%20Boolean%28f%29%20%2B%22y%22%29%3B%0A%20%20%0Aconst%20obj%20%3D%20%7Bprop%3A%20undefined%7D%3B%0Aconst%20g%20%3D%20obj.prop%3B%0Aconst%20h%20%3D%20obj.does_not_exist%3B%0Aconsole.log%28%22g%3A%20%22%2B%20typeof%20g%20%2B%22,%20%22%2B%20g%20%2B%22,%20%22%2B%20Boolean%28g%29%20%2B%22y%22%29%3B%0Aconsole.log%28%22h%3A%20%22%2B%20typeof%20h%20%2B%22,%20%22%2B%20h%20%2B%22,%20%22%2B%20Boolean%28h%29%20%2B%22y%22%29%3B%0A%0Aconst%20arr%20%3D%20%5Bundefined%5D%3B%0Aconst%20i%20%3D%20arr%5B0%5D%3B%0Aconst%20j%20%3D%20arr%5B1%5D%3B%0Aconsole.log%28%22i%3A%20%22%2B%20typeof%20i%20%2B%22,%20%22%2B%20i%20%2B%22,%20%22%2B%20Boolean%28i%29%20%2B%22y%22%29%3B%0Aconsole.log%28%22j%3A%20%22%2B%20typeof%20j%20%2B%22,%20%22%2B%20j%20%2B%22,%20%22%2B%20Boolean%28j%29%20%2B%22y%22%29%3B%0A&cumulative=false&curInstr=27&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)
```js
{
  // the way to get a null value
  const x = null;
  console.log("x: "+ typeof x +", "+ x +", "+ Boolean(x) +"y");

  // some of the ways to get an undefined value
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

__Resources__
* [undefined vs. null](https://www.educba.com/undefined-vs-null/)
* [null, undefined, not defined](https://medium.com/technoetics/difference-between-null-undefined-and-not-defined-in-javascript-3a52a62894b)
* [null, undefined, not declared](https://lucybain.com/blog/2014/null-undefined-undeclared/)


___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>
