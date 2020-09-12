# Required Function Parameters

JS is a loosely typed language,
so even if my function expects 2 parameters, who can force that?  

Today I stumbled upon a neat way to have the function throw an error if a parameter is missing.

First we define a helper function as so: 
```js
let isRequired = () => {
    throw new Error('This is a mandatory parameter.');
}
``` 

Then we assign the function as the default value for the required parameters.
Since default values are ignored when a value is passed, 
this function will only be invoked if the parameter is missing.

```js
let greetings = (name = isRequired(), message = 'Hello,') => {
    return `${message} ${name}`;
}
```

Now if we call this function without the first paramter, the result will be:
![Function error](./required-function-params_1.png)
