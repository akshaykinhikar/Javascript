
 ##### `__proto__`  vs `prototype`
  <details><summary><b>Answer</></summary>

  <ul>
  <li>__proto__ : its a chain, we use this to access prototype available</li>
  <li>prototype: is used to declare prototype on Object, function etc</li>
  </ul>  
  </details>




##### What is prototype chaining...
  ```javascript
function Person(f,l,age) {
    this.f = f;
    this.l = l;
    this.age = age;
}

Person.prototype.getDetails = function() {
    return `full name is ${this.f} ${this.l} and age is ${this.age}`
}

var AK = new Person("Akshay", "K", 32);
console.log(AK.getDetails());
console.log(AK.__proto__);
console.log(JSON.stringify(AK.__proto__.__proto__));
console.log(AK.__proto__.__proto__.__proto__);
  ```
  <details><summary><b>Answer</></summary>

  
  ```javascript
"full name is Akshay K and age is 32"
{
  getDetails: function() {
    return `full name is ${this.f} ${this.l} and age is ${this.age}`
}
}
"{}"
null
  ```
  </details>




##### Call Vs Bind Vs Apply       

<details><summary><b>Answer</></summary>
  <p>Call bind apply is used to pass context and bind value to javascript methods, objects</p>
  <p>When we want to send extra parameters to function</p>
  <p>Call</p>
  
  ```javascript
  var person = {
  name: "Akshay",
  handler : function(handler) {
  console.log(this.name + "==>" + handler);
  }
  }
  person.handler("do your work");
  person.handler.call({name: "nish"}, "do your work");
  
  VM6783:5 Akshay==>do your work
  VM6783:5 nish==>do your work
  ```
  
  <p>Apply</p>
  
  ```javascript
  var person = {
  name: "Akshay",
  handler : function(handler) {
  console.log(this.name + "==>" + handler);
  }
  }
  person.handler("do your work");
  person.handler.apply({name: "nish"}, ["do your work"]);
  
  VM6900:5 Akshay==>do your work
  VM6900:5 nish==>do your work
  ```
  
  
  <p>Bind</p>

  <li>Used in polymorphisom - overloading and overriding</li>
  <li>we use  class B extends class A and use bind to pass extra params</li>
  
  ```javascript
  var person = {
  name: "Akshay",
  handler: function(handler) {
  console.log(this.name + "==> " + handler);
  }
  
  }
  undefined
  person.handler("nothing")
  VM477:4 Akshay==> nothing
  undefined
  var nisha = person.handler.bind({name: 'nisha'})
  undefined
  nisha()
  VM477:4 nisha==> undefined
  undefined
  nisha("do your work");
  VM477:4 nisha==> do your work
  undefined
  ```
  
  </details>

  ##### Question
  ```javascript
  const user = {
        email: 'ak@gmail.com',
        updateEmail: email => {
            this.email = email;
        }
    }
    
    user.updateEmail('updatedEmail@gmail.com');
    
    console.log(user.email)

  ```
  <details><summary><b>Answer</></summary>

  
  ```javascript
ak@gmail.com

  ```
  </details>

  ##### Question
  ```javascript
const user = {
    email: 'ak@gmail.com',
    updateEmail: function(email) {
        this.email = email;
        return this.email;
    }
}

user.updateEmail('updatedEmail@gmail.com');

console.log(user.email)

  ```
  <details><summary><b>Answer</></summary>

  
  ```javascript
updatedEmail@gmail.com
  ```
  </details>


  
  ##### Question
  ```javascript
const animals = {};

let dog = {emoji: 'dog'};

let cat = {emoji: 'cat'}

animals[dog] = {...dog, name: 'jony'}

animals[cat] = {...cat, name: 'sara'}

console.log(animals[dog]);
  ```
  <details><summary><b>Answer</></summary>

  
  ```javascript
animals["[object object]"] = {emoji: '', name: ''}
{emoji: 'cat', name: 'sara'}

  ```
  </details>

  ##### Question
  ```javascript
const person1 = {name: 'Akshay'};

const members1 = [person1];

person1 = null;

console.log(members1);
  ```
  <details><summary><b>Answer</></summary>

  
  ```javascript
"<a class='gotoLine' href='#45:9'>45:9</a> Uncaught TypeError: Assignment to constant variable."
  ```
  </details>


  ##### Question
  ```javascript
let person = { name: 'Akshay' };

const members = [person];

person = null;

console.log(JSON.stringify(members));
  ```
  <details><summary><b>Answer</></summary>

  
  ```javascript
[{"name":"Akshay"}]
  ```
  </details>


  ##### Question
  ```javascript


let person = {name: 'Akshay'};

function getFullname(lastName) {
    return `Fullname is  ${this.name} ${lastName}`
}

console.log(getFullname.call(person, 'kinhikar'));
console.log(getFullname.bind(person, 'kinhikar'));


  ```
  <details><summary><b>Answer</></summary>

  
  ```javascript
Fullname is  Akshay kinhikar
ƒ ()
  ```
  </details>

  ##### Question
  ```javascript
console.log({ name: 'Akshay' } === { name: 'Akshay' })
  ```
  <details><summary><b>Answer</></summary>

  
  ```javascript
false
  ```
  </details>



  ##### Question
  ```javascript
function getArgs(one, two, three){

	console.log(one,two,three);

}



const str1 = "Hello";

const str2 = "World"



getArgs`${str1} is ${str2}`;
  ```
  <details><summary><b>Answer</></summary>

  
  ```javascript
["", " is ", ""], "Hello", "World" ?
  ```

<p>
This output is a result of using a tagged template literal with a function. In this case, the function is getArgs, and the template literal is ${str1} is ${str2}.
</p>


<p>When a tagged template literal is used, the function is called with two types of arguments: an array of string literals and the interpolated values. In this case, the array of string literals is ["", " is ", ""], and the interpolated values are "Hello" and "World".
</p>


  </details>




  ##### Question
  ```javascript
function Person(f,l,age) {
    this.f = f;
    this.l = l;
    this.age = age;
}

Person.prototype.getDetails = function() {
    return `full name is ${this.f} ${this.l} and age is ${this.age}`
}

var AK = new Person("Akshay", "K", 32);
console.log(AK.getDetails());
  ```
  <details><summary><b>Answer</></summary>

  
  ```javascript
full name is Akshay K and age is 32
  ```
  </details>


  ##### Question
  ```javascript
String.prototype.giveMePizza = () => {
    return 'Pizza'
}

const name = "lorem";

console.log(typeof name + "   " + name.giveMePizza())

  ```
  <details><summary><b>Answer</></summary>

  
  ```javascript
string   Pizza
  ```
  </details>



  ##### Question
  ```javascript
class Dog {
    constructor(name){
        this.name = name;
    }
}

Dog.prototype.bark = function() {
    console.log(`Woof I am ${this.name}`);
}

const pet = new Dog('Mara');
pet.bark();

delete Dog.prototype.bark;

pet.bark();



  ```
  <details><summary><b>Answer</></summary>

  
  ```javascript
Woof I am Mara
Uncaught TypeError TypeError: pet.bark is not a function


  ```
  </details>



  












































<H3>References: </H3>
<ul>
<li>https://www.youtube.com/playlist?list=PLWlZdiSk22n9-gcCsz-AZ8SkN-92W_599</li>
</ul>
