# Finding errors in a large JSON file

I received a large `.json` like file (actually a dump from MongoDB). 
24,000+ lines long, and more than 13 MB. 
Along with a requirement to convert it to google sheets. 

The file was looking something like this: 

```js
{"id":"sadf98","name":"Johnny",...} 
{"id":"sadf98","name":"Johnny",...}
{"id":"sadf98","name":"Johnny",...}
``` 

So I opened it in my favorite IDE (Webstorm) and was prompted by the IDE that the file is too big for linting.
Knowing that a real JSON file looks a bit different, 
I quickly added a comma to the first char of each line, 
and `[]` brackets at the beginning and end the file. 

Then I attempted to convert it with [an online converter](https://numidian.io/convert/json/to/csv).

But I got a very generic response that there is an error in my JSON.

How am I supposed to know where it is in the file?

[jsonlint](https://www.npmjs.com/package/jsonlint) to the rescue!

```bash 
$ npx jsonlint <path-to-file> 

Error: Parse error on line 28273: 
...":true,"instanceId":"VBQAF]
 -----------------------^
Expecting 'STRING', 'NUMBER', 'NULL', 'TRUE', 'FALSE', '{', '[', got 'undefined'
```

So the file was truncated in the middle. Fixed it, and could convert to CSV successfully.
