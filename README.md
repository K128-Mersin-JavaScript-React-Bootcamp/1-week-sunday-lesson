1. DOM Nedir?
    * Document Object Model

1. 1. scipt neden alta konur?
2. innerHTML
```html
<html>
<body>

<p id="demo"></p>

<script>
document.getElementById("demo").innerHTML = "Hello World!";
</script>

</body>
</html>
```
3. getElementsByTagName("p")
4. Chaining
```js
const x = document.getElementById("main");
const y = x.getElementsByTagName("p");
```
5. getElementsByClassName("intro")
6. Finding elements by CSS selectors
```js
const x = document.querySelectorAll("p.intro");
```
7. Form elemanlarının alınması
```html
<form action="/login" method="post" id="frm1">
    <input type="text" name="username" id="user" value="zafer">
    <input type="password" name="password" id="passw" value="1234">
</form>
<script>
const myForm = document.forms["frm1"];
let text = "";
for (let i = 0; i < myForm.length; i++) {
    text += myForm.elements[i].value;
}
console.log(text);
<script>
```
8. FormData()
```js
const myForm = document.forms["frm1"];
var object = {};
const formData = new FormData(myForm);
formData.forEach(function(value, key){
    object[key] = value;
});
var json = JSON.stringify(object);
```
9. Change attribute
```html
<img id="myImage" src="smiley.gif">

<script>
document.getElementById("myImage").src = "https://via.placeholder.com/140x100";
</script>
```
10. document.write
```html
<p>Bla bla bla</p>

<script>
document.write(Date());
</script>

<p>Bla bla bla</p>
<script>
window.addEventListener('DOMContentLoaded', (event) => {
    document.write(Date());
});
</script>
```
11. form validation
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
        input {
            display: block;
            margin-bottom: 5px;
        }
        .error {
            color:red;
            display: none;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>

    <form action="/login" method="post" id="frm1" onsubmit="return validateForm()">
        <input type="text" name="username">
        <span class="error">Please fill</span>
        <input type="password" name="password">
        <span class="error">Please fill</span>
        <input type="submit" value="Submit">
    </form>

    <script>
    function validateForm () {
        const myForm = document.forms["frm1"];
        let isSuccess = true;
        if(!myForm.username.value) {
            myForm.username.nextElementSibling.style.display = 'block';
            isSuccess = false;
        }
        if(!myForm.password.value) {
            myForm.password.nextElementSibling.style.display = 'block';
            isSuccess = false;
        }
        
        return isSuccess;
    }
    </script>

</body>
</html>
```
12. Automatic form validation
```html
    <form action="/login" method="post" id="frm1">
        <input type="text" name="username" required oninvalid="this.setCustomValidity('Enter User Name Here')">
        <span class="error">Please fill</span>
        <input type="password" name="password" required>
        <span class="error">Please fill</span>
        <input type="submit" value="Submit">
    </form>
```
13. Animation
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        img {
            width: 100px;
            height: 100px;
            position: absolute;
        }
    </style>
</head>
<body>
    <img id="car" src="car.png" alt="car">

    <script>
        const car = document.getElementById("car");
        let left = 0;
        const timer = setInterval(() => {

            car.style.left = `${left}px`;
            left+=10;
            if(left + 100 >= window.innerWidth) {
                clearInterval(timer);
            }
        }, 10)
    </script>
</body>
</html>
```
14. addEventListener
```js
document.getElementById("myBtn").addEventListener("click", alert(new Date));
```
15. Event bubbling
```html
<style>
  body * {
    margin: 10px;
    border: 1px solid blue;
  }
</style>

<form onclick="alert('form')">FORM
  <div onclick="alert('div')">DIV
    <p onclick="alert('p')">P</p>
  </div>
</form>
```
16. Add event handler to window
```js
window.addEventListener("resize", function(){
    document.getElementsByTagName("body")[0].innerHTML = window.innerWidth;
});
```
17. Create elements

```js
const paragraph = document.createElement("p");
const node = document.createTextNode("This is new.");
para.appendChild(node);
const element = document.getElementById("div1");
element.appendChild(para);
```

18. Remove elements
```html
<div id="div1">
  <p id="p1">This is a paragraph.</p>
  <p id="p2">This is another paragraph.</p>
</div>

<script>
const parent = document.getElementById("div1");
const child = document.getElementById("p1");
parent.removeChild(child);
</script>
```
19. History Api
```html
<button onclick="goToHello()">GoToHello</button>
<script>
    function goToHello() {
        const state = { 'page_id': 1, 'user_id': 5 }
        const title = 'Hellöö'
        const url = 'hello.html'
        history.pushState(state, title, url)
    }
</script>
```
20. Navigator API
21. Cookies
```js
        document.cookie = "username=John Doe; expires=Thu, 18 Dec 2021 12:00:00 UTC; path=/hello";
```

22. localStorage, sessionStorage(tab), websql, indexedDB
```js
localStorage.setItem("lastname", "Smith");
localStorage.getItem("lastname");
localStorage.removeItem("lastname");
```

23. Web Worker
```html
<div id="result"></div>

<script>
    let w;
    startWorker();
    
    function startWorker() {
      if(typeof(w) == "undefined") {
        w = new Worker("demo_workers.js");
      }
      w.onmessage = function(event) {
        document.getElementById("result").innerHTML = event.data;
      };
    }
    
    function stopWorker() { 
      w.terminate();
      w = undefined;
    }
</script>
```
24. Service workers
https://mdn.github.io/sw-test/
https://github.com/mdn/sw-test/blob/gh-pages/sw.js

25. Callbacks
```js
function sum(x, y, myCallback) {
    const result = x + y;
    myCallback(result)
}
sum(x, y, console.log);
```

26. Promise API
    * pending
    * fulfilled
    * rejected
```js
let myPromise = new Promise(function(myResolve, myReject) {
  setTimeout(function() { myResolve("Hello World"); }, 3000);
});

myPromise.then(function(value) {
  document.getElementById("demo").innerHTML = value;
});
```
27. Fetch API
```json
fetch("myFile.txt")
    .then(x => x.text())
    .then(x => document.write(x));
```

28. Async await
```js
async function myDisplay() {
  let myPromise = new Promise(function(myResolve, myReject) {
    setTimeout(function() { myResolve("Hello World"); }, 3000);
  });
  document.getElementById("demo").innerHTML = await myPromise;
}

myDisplay();
```
29. Generators
    * Kitap metaforu
```js
function* generator() {
  yield 1;
  yield 2;
  yield 3;
}

const gen = generator(); // "Generator { }"

console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
console.log(gen.next().value); // 3
```

```js
function* infinite() {
    let index = 0;

    while (true) {
        yield index++;
    }
}

const generator = infinite(); // "Generator { }"

console.log(generator.next().value); // 0
console.log(generator.next().value); // 1
console.log(generator.next().value); // 2
```

```js
function * iterableObj() {
  yield 'This';
  yield 'is';
  yield 'iterable.'
}
for (const val of iterableObj()) {
  console.log(val);
}
```

