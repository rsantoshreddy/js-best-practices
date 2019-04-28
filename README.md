# JS BEST PRACTICES

## Semicolon Insertion

JavaScript has a mechanism that tries to correct faulty programs by automatically inserting semicolons. Do not depend on this. It can mask more serious errors.

It sometimes inserts semicolons in places where they are not welcome. Consider the consequences of semicolon insertion on the return statement. If a return statement returns a value, that value expression must begin on the same line as the return:

```javascript
return
{
    status: true
};
```
This appears to return an object containing a status member. Unfortunately, semicolon insertion turns it into a statement that returns undefined. There is no warning that semicolon insertion caused the misinterpretation of the program. The problem can be avoided if the { is placed at the end of the previous line and not at the beginning of the next line:

```javascript
return {
    status: true
};
```

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
[W3C](https://www.w3.org/wiki/JavaScript_best_practices)</br>
[JavaScript: The Good Parts](https://www.amazon.in/JavaScript-Good-Parts-ebook/dp/B0026OR2ZY)
