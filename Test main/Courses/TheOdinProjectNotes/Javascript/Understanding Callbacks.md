
Callbacks seem to be a sticking point for people new to programming. Put simply, callbacks are functions that are passed into another function as an argument. With the many ways one can define a function in JavaScript, it's no wonder why callbacks get confusing.

## [](https://dev.to/i3uckwheat/understanding-callbacks-2o9e#anatomy-of-a-function)Anatomy of a Function

JavaScript has many ways of defining a function, but they all follow a similar pattern and have the same pieces, they just look a bit different. There is more technical terminology surrounding functions, but we are going to gloss over them for now. (If you are interested, feel free to look up "Function Declarations" and "Function Expressions").

### [](https://dev.to/i3uckwheat/understanding-callbacks-2o9e#normal-functions-named-functions)Normal Functions (Named Functions)

Normal functions, probably the first way you learned about creating functions. Understanding the anatomy of these will help you understand the other types of functions as well.  

```
function funkyFunction(music, isWhiteBoy) {
  if (isWhiteBoy) {
    console.log('Play: ' +  music);
  }
}
```

This is actually called a `function declaration` and is broken into a few parts.

1. The `function` keyword
    - This tells the JavaScript compiler you are making a named function
2. The name
    - This is the name of the function, and what you will use when you call it. It is also used in stack traces.
3. The parameters
    - everything between `(` and `)` is a parameter, these must be separated by commas if there is more than one. There may also be nothing between the `()` if the function does not take any parameters. The parenthesis are required.
4. The function body
    - This is where the function actually does something. This code gets run with whatever values are passed into the parameters.

Calling a function looks similar to declaring it. When you call the function, you type the name of the function and add `()` after. (without the `function` keyword and the body). Inside the `()` you may pass it the values you want the parameters you defined to represent. These `arguments` are used like variables inside the body of the function.  

```
// Calling a function
funkyFunction('that funky music', true);

// This prints "Play: that funky music" in the terminal.
```

### [](https://dev.to/i3uckwheat/understanding-callbacks-2o9e#anonymous-functions)Anonymous Functions

These are very similar to normal functions, with just a few differences. Anonymous functions are not 'named', and have a few different syntaxes. Even though they cannot have a name, they can be assigned to a variable. Even though when assigned to a variable they show up in stack traces, they are still considered an anonymous function. They may show up as 'anonymous function' in stack traces when passed into other functions as callbacks, however.

Anonymous functions are mostly used by passing them into other functions as a `callback`. This will become more clear later.

Each of the functions below are identical to the funkyFunction above in their 'funk-tionality'  

```
// This example is still an anonymous function even though we used the `function` keyword, as it doesn't have a name.
const funkyFunction = function(music, isWhiteBoy) {
  if (isWhiteBoy) {
    console.log('Play: ' +  music);
  }
}

// This is called an arrow function, we'll get into these soon.
const funkyFunction = (music, isWhiteBoy) => {
  if (isWhiteBoy) {
    console.log('Play: ' +  music);
  }
}
```

An anonymous function is just a function that does not have a name, this doesn't mean that it cannot be called. Each of the above functions can be called exactly the same way:  

```
funkyFunction('that funky music', true);
```

And this is because functions are 'first class citizens' in JavaScript and can be assigned to variables. Or passed as an argument to another function.

#### [](https://dev.to/i3uckwheat/understanding-callbacks-2o9e#arrow-functions)Arrow Functions

These are just a shorter way to write a function. They do have some special rules however, and understanding the rules imposed by arrow functions will help you understand callbacks. We're going to ignore the `this` binding rules for these functions for now.

- If there is only one argument, the parenthesis `()` can be omitted
- if arrow functions are one line, the brackets `{}` can be omitted.
    - When omitting the brackets, the arrow function returns the evaluated expression without requiring the `return` keyword.

The functions below are variations of the rules above  

```
const playThe = (funky) => {
  return funky + " music";
}

const playThe = funky => {
  return funky + " music";
}

const playThe = funky => funky + " music";

// You can call all of these functions like: `playThe('blues')`
```

Below are some examples of an arrow function without an argument. These functions are all identical as well. Notice the `()` in place of any named arguments. It is required because there aren't any parameters.  

```
const playThat = () => "funky music";

const playThat = () => { return "funky music"; }

const playThat = () => {
  return "funky music";
}
```

### [](https://dev.to/i3uckwheat/understanding-callbacks-2o9e#key-point)Key Point

Take some time and study the function examples above and note how they are similar and how the same parts exist in both, with the exception of the `function` keyword.

## [](https://dev.to/i3uckwheat/understanding-callbacks-2o9e#what-callbacks-look-like)What Callbacks Look Like

You most likely have seen, or even used, callbacks and not realized it. They are used frequently in JavaScript. Understanding JavaScript is impossible without understanding callbacks. Below is an example of something you may have run into before.  

```
const notes = ['do', 're', 'me'];

notes.forEach((note) => console.log(note));
```

This is the `forEach` array method. This method simply takes a `callback` function as its argument. (Don't forget that `forEach` is a function itself).

There are many other ways to do the same thing (as is tradition in JavaScript), below are a few more ways to write this code:  

```
const notes = ['do', 'ray', 'me'];

notes.forEach((note) => { 
  console.log(note);
});

notes.forEach(function(note) {
  console.log(note); 
});

// This one is tricky, but will make more sense later
notes.forEach(console.log); 
```

## [](https://dev.to/i3uckwheat/understanding-callbacks-2o9e#how-callbacks-work)How Callbacks Work

To state it once more: Callbacks are just functions passed into other functions as arguments (as a parameter).

### [](https://dev.to/i3uckwheat/understanding-callbacks-2o9e#iterator-functions)Iterator Functions

Below is what `forEach` might look like under the hood, notice it calls the `callback` function each time it loops over an item.  

```
function myForEach(array, callback) {
  for (let i = 0; i < array.length; i++) {
    callback(array[i]); // This is when the callback function gets called, or executed
  }
}

// You would call it like this:
const myArry = [2, 3, 4, 2];
myForEach(myArry, (item) => {
  console.log(item + 2); 
})
```

_WHOA, hold up. Where did `item` come from?_

This came from the function `myForEach` calling the callback with an argument. The line with `callback(array[i])` is calling the callback function with an argument, which we defined inline as an anonymous function. Below are more examples of how this could be called.  

```
const myArry = [2, 3, 4, 2];

// We do not need the `()` in this case, as we only have one argument and we are using an arrow function
myForEach(myArry, item => console.log(item + 2)); 

// We can pass arguments to this kind of anonymous function as well
myForEach(myArry, function(item) {  
  console.log(item + 2) 
});

// This time we are declaring the function we want to use as a callback
// Notice we define `item` as a parameter to be passed in when it's called by the `myForEach` function.
function printItemPlusTwo(item) {
  console.log(item + 2);
}

// `item` is passed into the function, we do not need to declare it here because we declared it elsewhere. 
// It is the same as the 'console.log' example above except we declared our own function.
myForEach(myArry, printItemPlusTwo); 
```

Another good example of how callbacks work might be the `.map` method (read more on MDN), below is one way it might be implemented.  

```
function myMap(array, callback) {
  const myNewArray = [];

  for (let i = 0; i < array.length; i++) {
    const callbackResult = callback(array[i]);
    myNewArray.push(callbackResult); 
  }

  return myNewArray;
}


// This could be called like this:
const addedArray = myMap([1, 2, 3], (arrayNum) => {
  return arrayNum + 2; 
});


// OR
const addedArray = myMap([1, 2, 3], (arrayNum) => arrayNum + 2)
```

### [](https://dev.to/i3uckwheat/understanding-callbacks-2o9e#event-listeners-dom)Event Listeners (DOM)

Event listeners in JavaScript seem to be confusing to people, but after understanding callbacks, these should be a lot easier to understand.

Let's review what they look like, see if you can pick out the different things going on.  

```
const element = document.querySelector("#myId");
element.addEventListener('click', (event) => {
  console.log(event.target.value);
  // `event` is passed into the callback from the `.addEventListener` function when it receives a 'click' event.
});
```

If you notice, the second argument (value you pass into a function) to `addEventListener` is a function. In this case it's an anonymous arrow function. This piece of code could have also have been written like this and it would behave identically.  

```
const element = document.querySelector("#myId");
element.addEventListener('click', function(event) {
  console.log(event.target.value);
});
```

Part of what confuses people is the `event` object. Where does it come from? How does it get there?

This event object is passed into the callback function by the `.addEventListener` function. A function is calling another function.

This is because.... Callbacks are just functions passed into another function as arguments.

That means we can declare a function outside of the argument list and just add it by its name as well. Like so:  

```
function myEventHandler(event) {
  // do something, probably with 'event'
}

const element = document.querySelector("#myId");
element.addEventListener('click', myEventHandler);
```

Notice how we didn't 'call' the function called `myEventHandler`? If we were to call it inside the parameter list, the function we called `myEventHandler` would run immediately and give the `addEventListener` the result of calling that function. (in this case, it would be undefined)

## [](https://dev.to/i3uckwheat/understanding-callbacks-2o9e#conclusion)Conclusion

Callbacks are an important part of JavaScript, they are vital to understand, even with the onset of promises and async/await. Callbacks get called by another function, so you don't have to call them in the arguments, ( Calling a function is using a function's name and adding `()` to the end of it, like `console.log()` )

These are something that you will learn if you give yourself time, understanding how they work will make your JavaScript career a lot easier!