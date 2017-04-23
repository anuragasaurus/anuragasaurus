---
title: Javascript basics - parsing-function-arguments
date: "2017-04-22T22:40:32.169Z"
layout: post
readNext: "/react-basics-making-markdown-parser/"
path: "/parsing-function-arguments/"
---

Hello guys, in this post I'm gonna talk about arguments objects.

So there are always two implicit arguments to all functions in javascript namely `arguments` and `this`. Value of `this` depends on how the function is called and value of `arguments` is an array with all the arguments as values.

```javascript
var sampleFunc = function(){
	console.log(this, arguments);
}

sampleFunc(1,2,3);

/**
Window {stop: function, open: function, alert: function, confirm: function, prompt: function…}
[1, 2, 3, callee: function, Symbol(Symbol.iterator): function]
**/
```

As you can see `arguments` prints an array with value 1,2,3 and some other things. Now the important thing - the `arguments` is not an array, it's actually an object which lokks like an array. It does not have array methods like `slice`, `shift`, `push` etc.

So it would be a good idea to convert `arguments` into an array which we can do like this,

```javascript
var sampleFunc = function(){
	var arg = Array.prototype.slice.call(arguments);

	//or

	var arg = [].slice.call(arguments);

	console.log(arg);
}

sampleFunc(1,2,3);
//[1, 2, 3]
``` 

So this is what `arguments` is and how you can use it.