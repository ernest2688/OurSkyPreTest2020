Question code
----------------
```
function createArrayOfFunctions(y) {
  var arr = [];
  for(var i = 0; i<y; i++) {
   arr[i] = function(x) { return x + i; } //problem
  }
  return arr;
}
```

*************************
The main problem is that the i in the for loop is is not in scope of the return x+i.
So the result will always be x+y but not x+i.

By stackoverflow. In ES6, we can simply use let keyword in stead of var to make the i in scope.
*************************

Possible solution
----------------------
```
function createArrayOfFunctions(y) {
  let arr = [];
  for (let i = 0; i < y; i++) {
    arr[i] = function(x) {
      return x + i;
    };
  }
  return arr;
}
```

Reference:
https://stackoverflow.com/questions/44015982/how-to-check-the-index-of-a-function-in-an-array-of-functions-in-javascript
https://stackoverflow.com/questions/750486/javascript-closure-inside-loops-simple-practical-example
