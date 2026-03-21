---
title: "Javascript In's and Outs"
seoTitle: "ins and outs of javascript | understading javascript deeper | core js"
seoDescription: "this is a document that i created out of the tools i have used and realized i needed javascript | understanding other js concepts | clean & important js ski"
datePublished: 2022-07-19T08:51:00.896Z
cuid: cl5rxrmql01u1onnv1auragm5
slug: javascript-ins-and-outs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1657988654357/6z6Oo7SP1.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1657988959515/kNupNzNn0.png
tags: programming-blogs, javascript, webdev, junior-developer, basicjs

---

# Javascript Cheatsheet:

## Javascript Strings

### String Access:

- Accessing characters `.chartAt()`, `'dog'.chartAt(1) ` returns 0.

- `.chartAt(index);` takes an index which starts at 0 and returns the character at that index.
- `.chartAt(start, finish)` will returns character at start to finish position.

 ### String Search:

- ` .indexOf(searchValue[fromIndex]) ` will help you search for for sub string within a string.

- this function takes string to be searched and optional parameter for the starting index for the search & -1 if nothing is found. 

- the function ` .startsWith(?) ` will help you find out what the string starts with.

- the function ` .endsWith(?) ` will returns true if the string ends with the parameter string.

- to replace a string we use the function ' .replace('str1','str2')'

- To check the occurance of a search string simply check if -1 was returned  from `.indexOf(?)`.

```javascript
    var str = 'hey there Batch';
    var count = 0;
    var pos = str.indexOf('a');
    while(pos != -1){
        count++;
        pos = str.indexOf('a', pos + 1)
    }
```

## Regular Expressions:

### Basic Regex:

- ` ^ ` start of a string
- ` \d: ` finds any digit
- ` [abc] ` finds an character between the brackets
- ` [^abc]` finds character not in the bracket
- ` [0 - 9]` finds digit between the bracket
- ` [^0 - 9]` finds digit not between the bracket
- ` (x|y)` finds any of the alternatives specified

## RegExp functions:

- ` search(?) ` test for matches in a string and returns the index of the match.
- ` match(?) ` test for matches in a string and returns all the matches.
- ` exec(?) ` returns the first match.
- ` test(?) ` returns true of false.

```javascript
    var str = 'hey there Batch';
    var cn = str.search(/here/);
    console.log(cn);
    
```

## Objects:

## Base64 Encoding:

- The ` btoa(?) ` function creates a base64 encoded ASCII string from the string. 
- The ` atob(?) ` function will decode the base64 encoded string.

## String Shortening:

```
var Dictionary = "sjhlksafhjksdhfjkdsflsdjlifhisdoncmx.nvmcx,grdj".split("");
```


```javascript
    function encoded(num) {
        var base = DICTIONARY.length
        var encoded="";

        if(num == 0){
            return DICTIONARY[0];
        }else{
            while(num > 0){
                encoded += DICTIONARY[(num % base)];
                num = Math.floor(num /base);
            }
        }

        return reverseWord(encoded);
    }

    function reverseWord(str){
        var reversed ="";
        for ( var i= str.length - 1; i >=0; i-- ){
            reversed +=str.charAt(i);
        }

        return reversed;
    }

    function decodeId(){
        var base = DICTIONARY.length;
        var decoded = 0;
        for (var index =0; index < id.split('').length; index++ ){
            decoded = decoded*base + DICTIONARY;
            indexOf(id.chartAt(index));
        }

        return decoded;
    }

```

## Javascript Arrays:

> ` var arr = [1, 2, 3 . 4] `.

- To access array elements we use its index ` arr[?] `

- To insert an array element `arr.push(?)`

- To remove an element at the end `arr.pop(?)` another option to remove is ` arr.shift(?) `


## Iteration:

- this method of iteration will call indices individually, and you will access the data inside it.

```javascript
    var arr = [1,2,3];

    for(var index in arr){
        console.log(arr[index]);
    }

```

- this method will allow you to access and use the objects of the array individually each time you get one, you can do your checks this way.

```javascript
    var arr = [1,2,3];

    for(var element of arr){
        console.log(element);
    }

```

### forEach():

- this method is better than the other iteration methods because it can break out of the iteration or skip certain elements of the array.  

```javascript
    var arr = [1,2,3];

    arr.forEach((el, in) => {
        console.log(el);
    }
    )
```

## Array Helper Functions:

- ` .slice(begin,end) ` will return us a portion of a given array taking the begining and end index of what you selecting.

```javascript
    var arr = [1, 2, 3, 4, 5];
    arr.slice(1, 2); // returns [2] 
    arr.slice(2, 4); // returns [3, 4]
```

- ` .from() ` function will help us to create a new array from an existing one.

```javascript
    var arr = [1, 2, 3, 4, 5];
    var arr2 = Array.from(arr);
```

- ` .splice() ` takes three params: begining & end index with number of things in the middle.After aplying the method the added other items will change the array.

```javascript
    var arr = [1, 2, 3, 4, 5];
    arr.splice(); // returns [] 
    arr.splice(1, 2); // returns [2, 3], modifying arr = [1,4]
    arr.splice(1,2,5,6,7) // returns [2, 3], arr = [1, 5, 6, 7, 4] 
```

- ` .concat(?) ` will be used to add another array into an existing one. The method will return a modified array but stull the original one remains untouched.

```javascript
    var arr = [1, 2, 3, 4, 5];
    arr.concat([1, 2]); // returns [1, 2, 3, 4, 5, 1, 2] and arr still remains the same
```

## Spread Operator:

- this operator will allow use to access all elements individually.


```javascript
    var arr = [1, 2, 3, 4, 5];

    function printNumz(a, b, c, d){
        return a + b + c + d;
    }
    console.log(printNumz(...arr))
```

## Array functional methods:

- The ` .filter() ` method is used for filtering elements or checking a condition like the following example:

```javascript
    var arr = [1, 2, 3, 4, 5];
    arr.filter(function (item) {
        return item > 2;
    }); // returns [3,4,5] 
    
```

- This method can allow you to perform other operations to the elements as you reach them in the erray.

- We also have the ` .reduce() ` function that will combine all the elements in the erray into one value, using the passed function.

```javascript
    var sum = [1, 2, 3, 4, 5].reduce(function(prevVal, currVal, index, array){
        return prevVal + currVal;
    });
    
```

## Cookies:

- to check if cookies are enabled we use the pattern with corresponding code to set the cookie, note that it might not work for older browsers.

```javascript
    if(navigation.cookieEnabled === False) {
        // Do something...
    }
    
    var COOKIE_NAME = 'Example cookie'; // naming the cookie.
    var COOKIE_VALUE = 'Something '; // the value of the cookie.
    var COOKIE_PATH = '/foo/bar'; // GIVE THE COOKIE A PATH.
    var COOKIE_EXPIRES;

    COOKIE_EXPIRES = (new Date(Date.new() + 6000 )). toUTCString();

    document.cookie += COOKIE_NAME + "=" + COOKIE_VALUE + "; expires=" + COOKIE_EXPIRES + "; path=" + COOKIE_PATH;
```

- ## Reading the cookie:

```javascript
    var name = name + "=" + cookie_array = document.cookie.split(';'),
    cookie_value;
    for (var i = 0; i<cookie_array[i].length; i++){
        var cookie = cookie_array[i];
        while(cookie.charAt(0) == ''){
            cookie = cookie.substring(1, cookie.length);
        }
        if(cookie.indexOf(name) == 0){
            cookie_value = cookie.substring(name.length, cookie.length);
        }
    } 
    
```

- LocalStorage, sessionStorage are like js objects, so we can use them like they are:

```javascript
   localStorage.greet = 'hey there'; // window.localStorage.setItem('')

   localStorage.greet; // window.localStorage.getItem('')

   delete localStorage.greet; // Same as: window.localStorage.removeItem('')
    
```

- sessionStorage uses the same storage as the localStorage but it will only be avaliable per session or for that window.

## Web Workers:

- a web worker is a way to run scripts  in background threads ` var webworker = new Worker("./path/to/webworker.js"); `

- you can also inject a script as a worker in a string the string is used in `URL.createObjectURL()`:

```javascript
   
    var workerData = "function someFunction() {}; console.log('More code');";
    var blobURL = URL.createObjectURL(new Blob(["(" + workerData + ")"], { type: "text/javascript" }));
    var webworker = new Worker(blobURL);

```

- service worker is a event-driven worker bound to the original site, it can control the site, and use its resources.

- ITS A PROGRAMMABLE NETWORK PROXY,
- IT WILL BE TERMINATED WHEN NOT IN USE.
- IT HAS A LIFE CYCLE UNBOUND TO THE WEB PAGE.
- IT NEEDS HTTPS.

