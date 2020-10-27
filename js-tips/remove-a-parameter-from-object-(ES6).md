# Remove a parameter from object (ES6)

We all know (hopefully), that it is not a good idea to save or return to the user a sensitive field like the password.

Here is a convenient use of the `ES6 spread operator` to strip the password property from the user object before returning it.

```js
const { password, ...result } = user;
return result;
```
