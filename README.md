
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
