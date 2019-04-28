# JS BEST PRACTICES

## Optimize loops

Loops can become very slow if you don’t do them right. One of the most common mistake is to read the length attribute of an array at every iteration:

```javascript
var names = ['George','Ringo','Paul','John'];
for(var i=0;i<names.length;i++){
  doSomeThingWith(names[i]);
}
```

This means that every time the loop runs, JavaScript needs to read the length of the array. You can avoid that by storing the length value in a different variable:

```javascript
var names = ['George','Ringo','Paul','John'];
var all = names.length;
for(var i=0;i<all;i++){
  doSomeThingWith(names[i]);
}
```

An even shorter way of achieving this is to create a second variable in the pre-loop statement:

```javascript
var names = ['George','Ringo','Paul','John'];
for(var i=0,j=names.length;i<j;i++){
  doSomeThingWith(names[i]);
}
```
Another thing to ensure is that you keep computation-heavy code outside loops. This includes regular expressions and — more importantly — DOM manipulation. You can create the DOM nodes in the loop but avoid inserting them into the document. You’ll find more on DOM best practices in the next section.

### References
[W3C](https://www.w3.org/wiki/JavaScript_best_practices)
