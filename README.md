# REPL.IT Links

- Factory - https://repl.it/@DotunLonge/LividThisNorthernhairynosedwombat
- Singleton - https://repl.it/@DotunLonge/KnowingAdmirableCock
- Bridge Pattern - https://repl.it/@DotunLonge/CraftyFrighteningSable
- Composite Pattern - https://repl.it/@DotunLonge/DeepskyblueConstantGoitered
- Flyweight Pattern - https://repl.it/@DotunLonge/IntentionalCalculatingSaltwatercrocodile

# Design Patterns

### What are Design Patterns?

Design pattern are reusable solutions to problems that occur frequently when designing a software. They can also be seen as templates for solving specific problems.

A pattern is represented in form of a rule that establishes a relationship between:

- A context
- A system of forces that arises in that context
- A configuration that allows the forces to resolve themselves in that context

#### Why is there a need to use them?

- The patterns are solid approaches to solving problems in software development and they provide proven solutions to problems because they are created from the minds of experienced developers
- The patterns can be easily reused
- The patterns have a set structure and vocabulary that can be used to express large solution  in the simplest form

#### Advantages of using patterns

- It helps to prevent minor issues that can cause serious problems in software development
- It helps to develop solutions that is not limited to a specific problem, hence the reusable concept
- It helps to avoid repetition in coding (the DRY style) which in turn reduces file size
- Patterns also help to develop the vocabulary of the programmer which would make communication faster
- Solutions developed with a pattern can be continually made better by other developers

Christopher Alexander claims that a pattern should be both a process and a thing, in essence, the process should create the thing.

Every pattern goes through a vetting process called the ‘Pattern’ity test

A Proto-pattern is one that has not yet been known to pass the ‘Pattern’ity test. Brief descriptions or snippets of proto-patterns are called patlets.

When is a pattern considered to be a good pattern?

- It solves a specific problem
- The solution is not an obvious one
- The concept described about the pattern must be a proven one

For a pattern to be valid, it should display recurring phenomenon which can be qualified in 3 key areas referred to as the Rule of 3

- Fitness of purpose shows how the pattern is considered successful
- Usefulness that shows the pattern is considered successful
- Applicability checks if it has a wide range of application that would make it worth enough to be called a Pattern

##### Categories of Design pattern

- Creational pattern focuses on how to creates objects or classes

- Structural pattern focuses on how to manage relationship between objects so that the application is created in a scalable way

- Behavioral pattern focuses on communication between objects.

  ​

### Creational Patterns

Creational pattern focuses on how to create objects or classes. Some creational patterns include:

- Factory pattern
- Singleton pattern

### Factory Method pattern

The factory pattern can be classified as a creational pattern. It deals with the problem of creating object without the need to specify the exact class of the object being created.

The factory pattern suggest defining an interface for creating an object where you allow the subclasses to decide which class to instantiate. It does this by defining a completely separate method for the creation of objects and which sub classes are able to override so that we can specify the type of object to be created.

When is it suitable to use?

- When the object setup requires a high level of complexity
- When there is a need to generate different instances depending on the environment
- When you are working with several small objects that share the same properties

```
function factory (){

    this.getIPhone = (type) => {

        let phone;

        if (type === "iPhone6") {

            phone = new iPhone6();

        } else if (type === "iPhone6s") {

            phone = new iPhone6s();

        } else if (type === "iPhone7") {

            phone = new iPhone7();

        } else if (type === "iPhoneX") {

            phone = new iPhoneX();

        }

        phone.type = type;

        phone.sayPrice = function(){

            console.log(this.type + " price: " + this.price + " naira" );

        }

        return phone;

    }

}

function iPhone6 (){

    this.price = "150000";

}

function iPhone6s (){

    this.price = "180000";

}

function iPhone7 (){

    this.price = "250000";

}

function iPhoneX (){

    this.price = "350000";

}

let phones = [];

var factory1 = new factory();

phones.push(factory1.getIPhone("iPhone6"));

phones.push(factory1.getIPhone("iPhone6s"));

phones.push(factory1.getIPhone("iPhone7"));

phones.push(factory1.getIPhone("iPhoneX"));

for (let i = 0; i < phones.length; i++) {

    phones[i].sayPrice();

}
```

Singleton Pattern

Singleton pattern can be implemented by creating a class with a method that creates a new instance of the class if one doesn't exist. In the event of an instance already existing, it simply returns a reference to that object.

It restricts instantiation of a class to a single object. With JavaScript, singletons serve as a namespace provider which isolate implementation code from the global namespace so-as to provide a single point of access for functions. It is not the object or 'class' that's returned by a singleton, it's a structure. In its simplest form, a singleton in JS can be an object literal grouped together with its related methods and properties. it's quite useful when exactly one object is needed to coordinate patterns across the system.

Example

- ```
  var mySingleton = {

     property1: "something",

     property2: "something else",

      method1: function () {

          console.log('hello world');

     }

  };

  var mySingleton = function () {


  var privateVariable = 'something private';

  	function showPrivate() {
          console.log(privateVariable);
        }


  return {
          publicMethod: function () {
  		showPrivate();
          },
                publicVar: 'the public can see this!'
  };
         };

                    var single = mySingleton();
                    single.publicMethod();
                    console.log(single.publicVar); 

  ```

  ​

### Structural Patterns

Structural pattern focuses on how to manage relationship between objects so that the application is created in a scalable way. Some structural patterns include:

- Bridge pattern
- Composite pattern
- Decorator pattern
- Flyweight pattern
- Façade pattern





### BRIDGE PATTERN:

The bridge pattern allows two components, which is the client and a service to work together with each components having its own interface. Bridge is therefore a high-level architectural pattern and its main goal is to write better codes through two levels of abstraction. Hence it facilitates very loose coupling of objects which is sometimes referred to as a double Adaptive pattern.

An example of the Bridge pattern is an application (the client) and a database driver (the service). The application writes to a well-defined database API, for example ODBC, but behind this API you will find that each driver's implementation is totally different for each database vendor (SQL Server, MySQL, Oracle, etc.).

Code snippets to explain the bridge pattern:

- ```
  // input devices
   
  var Gestures = function (output) {
      this.output = output;
   
      this.tap = function () { this.output.click(); }
      this.swipe = function () { this.output.move(); }
      this.pan = function () { this.output.drag(); }
      this.pinch = function () { this.output.zoom(); }
  };
   
  var Mouse = function (output) {
      this.output = output;
   
      this.click = function () { this.output.click(); }
      this.move = function () { this.output.move(); }
      this.down = function () { this.output.drag(); }
      this.wheel = function () { this.output.zoom(); }
  };
   
  // output devices
   
  var Screen = function () {
      this.click = function () { log.add("Screen select"); }
      this.move = function () { log.add("Screen move"); }
      this.drag = function () { log.add("Screen drag"); }
      this.zoom = function () { log.add("Screen zoom in"); }
  };
   
  var Audio = function () {
      this.click = function () { log.add("Sound oink"); }
      this.move = function () { log.add("Sound waves"); }
      this.drag = function () { log.add("Sound screetch"); }
      this.zoom = function () { log.add("Sound volume up"); }
  };
   
  // logging helper
   
  var log = (function () {
      var log = "";
   
      return {
          add: function (msg) { log += msg + "\n"; },
          show: function () { alert(log); log = ""; }
      }
  })();
   
  function run() {
   
      var screen = new Screen();
      var audio = new Audio();
   
      var hand = new Gestures(screen);
      var mouse = new Mouse(audio);
   
      hand.tap();
      hand.swipe();
      hand.pinch();
   
      mouse.click();
      mouse.move();
      mouse.wheel();
   
      log.show();
  }
  ```

  ​

Diagram to explain the bridge pattern:

​	

The objects participating in this pattern are:
client: in the above code : the run () fuction calls into abstraction to request an operation

Abstraction: in the above code it declares an interface for the first level abstraction and maintains a reference to the implementor.

Redefined Abstraction: in the above code mouse, gestures implements and extends the interface defined by Abstraction

Implementor: in the above code it declares and interface for second level or implementor abstraction

Concrete implementor: in the above code screen, audio implements the implementor interface and defines its effects.

### Composite Pattern

The composite pattern can be classified as a structural pattern. Composite pattern emphasizes that a group of objects can be treated in the same way you treat an individual object of the group. It is even a commonly used pattern.

Composite pattern compose objects into tree structures to represent part-whole hierarchies.

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>repl.it</title>
    <link href="index.css" rel="stylesheet" type="text/css" />
  </head>
  <style>
    .newClassAdded {
      color: red;
    }
  </style>
  
  <body>
      <div class="car">
          <h1>This is a Mercedes</h1>
      </div>    
    
      <div class="car">
          <h1>This is a Range Rover</h1>
      </div>    
  
      <div class="car">
          <h1>This is a Limo</h1>
      </div>
      
      <div id="ferari">
          <h1>This is a Ferari</h1>
      </div>
 
 
 <script
  src="https://code.jquery.com/jquery-3.2.1.min.js"
  integrity="sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4="
  crossorigin="anonymous"></script>
  
    <script>
     $('.car').addClass('newClassAdded');
     $('#ferari').addClass('newClassAdded');
      
    </script>
 
  </body>
</html>


```



### Decorator Pattern

The *decorator pattern *is a structural design pattern that promotes code reuse and is a flexible alternative to subclassing. This pattern is also useful for modifying existing systems where you may wish to add additional features to objects without the need to change the underlying code that uses them.

Traditionally, the decorator is defined as a design pattern that allows behavior to be added to an existing object dynamically. Using decorator objects is a flexible alternative to creating subclasses. The most important feature of the decorator is that it can be used in place of its component.

Ways a decorator modifies its components

The purpose of the decorator is to somehow modify the behavior of its component object.

- Adding behavior after a method: This is the most common way of modifying the method. The component’s method is called and some additional behavior is executed after it returns.


- Adding behavior before a method: If the behavior is modified before executing the component’s method, either the decorator behavior must come before the call to the component’s method, or the value of the arguments passed on to that method must be modified somehow.


- Replacing a method: This allows you to replace a method entirely in order to implement a new behavior.


- Adding new method: A decorator can be used to define new methods, but this becomes tricky to implement in a robust manner. In order to use this new method, the surrounding code must first know it is there. Since it is not in the interface, and since this new method is added dynamically, type checking must be done to identify the outermost decorator wrapping the object. It is much easier and less error-prone to modify the existing methods instead of decorating the component object with new methods because then the object can be treated the same way as before, with no modifications needed to the surrounding code. That being said, adding new methods with decorators can be an extremely powerful way of adding functionality to a class.

EXAMPLES

```
*// What we're going to decorate*

function MacBook() {

this.cost = function () { return 997; };

this.screenSize = function () { return 13.3; };

}

*// Decorator 1*

function Memory( macbook ) {

var v = macbook.cost();

macbook.cost = function() {

return v + 75;

}

}

*// Decorator 2*

function Engraving( macbook ){

var v = macbook.cost();

macbook.cost = function(){

return v + 200;

};

}

*// Decorator 3*

function Insurance( macbook ){

var v = macbook.cost();

macbook.cost = function(){

this.model = modelName;

}

truck.setColor = function( color ){

this.color = color;

}

*// Test the value setters and value assignment works correctly*

truck.setModel('CAT');

truck.setColor('blue');

console.log(truck);

*// vehicle:truck, model:CAT, color: blue*

*// Demonstrate 'vehicle' is still unaltered*

var secondInstance = new vehicle('car');

console.log(secondInstance);

*// as before, vehicle: car, model:default, license: 00000-000*


```

When to use decorator

Decorators should be used whenever you need to add features or responsibilities to a class and it is impractical to subclass it. The most common reason that subclassing is impractical is when the number and combinations of needed features require large numbers of subclasses.

 The decorator pattern should also be used when you want to add features to an object without having to change the code that uses it. Since decorators can modify objects dynamically and transparently, they are perfect for modifying existing systems. It can often be easier to create and apply a few decorators than it is to go through the trouble of creating and maintaining a subclass.

Drawbacks

There are two main drawbacks to using the decorator pattern. 

The first is that any code that relies on type checking will fail if an object has been wrapped with a decorator. It’s true that strict type checking of objects is rarely done in JavaScript, but if it is done in your code, decorators will not match the required type. Decorators are normally completely transparent to the client code; but this is one case where the client code will be able to tell the difference between a decorator and its component.

The second drawback is that using decorators can often complicate your architecture.

They have a tendency to introduce a lot of small objects that look relatively similar but do very different things. They can often be confusing, especially to developers not familiar with the decorator pattern. Also, the syntax required to implement decorators with dynamic interfaces can be frightening at best. You must use extra care when creating an architecture that uses decorators to ensure that your code is well-documented and easy to understand.

### Flyweight Pattern

The flyweight pattern saves memory by sharing large numbers of fine-grained     objects   effectively. Shared flyweight objects cannot be changed as they represent the characteristics that are shared with other objects.

Flyweight is known as an ‘object normalization technique’, this means that common properties are factored out into shared flyweight objects. The idea is similar to data normalization, which attempts minimize redundancy.

Examples of flyweight pattern include characters and line-styles in a word processor, or 'digit receivers' in a public switched telephone network application. You will find flyweights mostly in utility type applications such as word processors, graphics programs, and network apps; they are less often used in data-driven business type applications.

An example of the Flyweight Pattern is within the JavaScript engine itself which maintains a list of immutable strings that are shared across the application.

Code snippets to explain flyweight pattern

- ```
  	function Flyweight (make, model, processor) {
  	  this.make = make;    
  	  this.model = model;  
  	  this.processor = processor; }; 
  	  
  	  var FlyWeightFactory = (function () { 
  	    var flyweights = {};
  	    return { 
  	      get: function (make, model, processor) {
  	        if (!flyweights[make + model]) { 
  	          flyweights[make + model] = new Flyweight(make, model, processor);}
  	          return flyweights[make + model];       
  	          },        
  	          getCount: function () {  
  	            var count = 0;   
  	            for (var f in flyweights) count++;           
  	            return count;        
  	            
  	          }    
  	      
  	    } })();
  	    
  	    function ComputerCollection () { 
  	      var computers = {};  
  	      var count = 0;    
  	      return {       
  	        add: function (make, model, processor, memory, tag) {           computers[tag] = new Computer(make, model, processor, memory, tag);            count++;        
  	          
  	        },        
  	        get: function (tag) {  
  	          return computers[tag];      
  	          },      
  	          getCount: function () { 
  	            return count;        
  	            
  	          }   
  	          }; 
  	      
  	    }   
  	    
  	    var Computer = function (make, model, processor, memory, tag) { 
  	      this.flyweight = FlyWeightFactory.get(make, model, processor); 
  	      this.memory = memory;  
  	      this.tag = tag;   
  	      this.getMake = function () { 
  	        return this.flyweight.make;
  	        }    
  	        }  
  	       var log = (function () {
  	         var log = "";      return {
  	           add: function (msg) { log += msg + "\n"; },
  	           show: function () { alert(log); log = ""; } 
  	           } })();
  	           function run() { 
  	             var computers = new ComputerCollection(); 
  	             computers.add("Dell", "Studio XPS", "Intel", "5G", "Y755P");    computers.add("Dell", "Studio XPS", "Intel", "6G", "X997T");    computers.add("Dell", "Studio XPS", "Intel", "2G", "U8U80");    computers.add("Dell", "Studio XPS", "Intel", "2G", "NT777");    computers.add("Dell", "Studio XPS", "Intel", "2G", "0J88A");    computers.add("HP", "Envy", "Intel", "4G", "CNU883701");    computers.add("HP", "Envy", "Intel", "2G", "TXU003283");  
  	             
  	             log.add("Computers: " + computers.getCount());
  	             log.add("Flyweights: " + FlyWeightFactory.getCount());
  	             log.show();}
  ```

  ​

Diagram to explain how flyweight pattern works:

In the above code we are building computers. Many models, makes, and processor combinations are common, so these characteristics are factored out and shared by Flyweight objects.

The Flyweight Factory maintains a pool of Flyweight objects. When requested for a Flyweight object the Flyweight Factory will check if one already exists; if not a new one will be created and stored for future reference. All subsequent requests for that same computer will return the stored Flyweight object.

Several different computers are added to a Computer Collection. At the end we have a list of 7 Computer objects that share only 2 Flyweights. These are small savings, but with large datasets the memory savings can be significant.

The log function is a helper which collects and displays result

The objects participating in this pattern are:

Client: In above code, the computer calls into flyweight factory to obtain flyweight objects

Flyweight Factory: In above code, flyweight factory creates and manages flyweight objects if requested, and if a flyweight object does not exist it creates one, and stores newly created flyweights for feature requests.

Flyweight: In above code, flyweight maintains intrinsic data to be shared across the application



### Façade Pattern

The façade pattern is kind of like a concealer pattern. It cn also be classified as a structural pattern of design. It presents a simple outlook to the world while hiding the underlying complexity.

The façade pattern is an interface that shields client from complex functionality in one or more subsystems. It is often present in systems that are built around a multi-layer architecture.

A framework like jQuery uses the façade pattern of development.

```
var loan = (receiver) =>{
this.receiver = receiver;
}

loan.prototype = {
  getLoan: (amount)=>{
  var result = "approved";
  if (! new database().verify(this.receiver) ) {
      result = "denied";
  }else if (! new inDebt().check(this.receiver) ) {
      result = "denied";
  }
  return this.receiver + " has been " + result + " the loan of " + amount;
  }
}

var database = () =>{
this.verify = (receiver)=>{
//complex code
return true;
}
}

var inDebt = () =>{
this.check = (receiver)=>{
//complex code
return true;

}

}

var dele = new loan ("Dele");
var output = dele.getLoan("10000naira");
console.log(output);
```



### Behavioral Patterns 

Behavioral pattern focuses on communication between objects. Some behavioral patterns include:

- Observer pattern
- Chain of responsibility pattern
- Command pattern

Observer Pattern

The observer pattern can be categorized as a behavioral pattern. It is popularly known as the publish/subscribe pattern. It is a design pattern that allows an object to known as the subscriber to watch another object known as the publisher so when the publisher changes state, the subscriber(s) are notified and updated automatically. It is a popularly used design pattern.

At the point when the subscriber is no longer interested in listening to the publisher, the publisher can remove it from the update list.

The addEventListener is a simple example of an observer.

HTML Code 

```
<button class="myButton">Click Me</button>

Javascript Code

var button = document.querySelector('.myButton');

button.addEventListener("", ()=>{
 console.log("hello");
})
```



#### Chain Of Responsibility Pattern

A chain of responsibility consists of several different types of objects. It allows you to decouple the sender and the receiver of a request. 

The *sender *is the object that makes the request. The *receivers *are the objects in the chain that receive this request and handle it or pass it on. The request itself is sometimes an object, encapsulating all of the data associated with the action. The typical flow looks something like this:

- The sender knows of the first receiver in the chain. It will send a request to that first receiver.
- Each receiver will analyze the request and either handle it or pass it on.
- Each receiver only knows about one other object, its successor in the chain.
- If none of the receivers handles the request, it falls off the chain, unhandled. Depending on the implementation, this can either happen silently, or it can cause an error to be thrown.

To pass on request on to the chain, the most common are either to use a dedicated request object, or to use no argument at all and rely on the method invocation itself to pass the message. The simplest way is to just call the method with no argument.

When should chain of Responsibility be used?

There are several situations where the chain of responsibility should be used. In the library example, you wanted to issue a request for a book to be sorted. You didn’t know ahead of time which catalog it would be sorted into, if any. You also didn’t know how many or what type of catalogs might be available. To solve these problems, you used a chain of catalogs, each passing the book object down the chain to its successor. That example illustrates the situations that would benefit from the chain of responsibility. It should be used in situations where you don’t know ahead of time which of several objects will be able to handle a request. It should also be used if that list of handler objects isn’t known at development time and will be specified dynamically. The chain of responsibility can also be used if more than one object should handle each request. In the library example, for instance, each book can be sorted into more than one catalog. The request can be handled by an object and can then continue to be passed on, possibly to be handled by another object further down the chain. This pattern allows you to decouple specific, concrete classes from your clients, and instead specify a chain of loosely coupled objects that will implicitly handle the request. It helps to make your code more modular and maintainable.

Command Pattern

This pattern encapsulates (wraps up) actions as objects. Command objects allow for loosely coupled systems it separates the objects that issue a request from the objects that actually process the request. These requests are called events and the code that processes the requests are called event handlers.

​	

For example if you want to build an application that supports copy, cut, and paste clipboard actions. These actions can be triggered in different ways throughout the app: by either a context menu or by a menu system for example when you right click on a textbox, or a keyboard shortcut. Command objects allows you to centralize the processing of these actions one for each operation. So you need only one command for processing all Copy requests, one for all Cut requests, and one for all Paste request. This happen because commands centralizes all processing also frequently involved in handling Undo functionality for the entire application.

 

### Code snippets to explain command pattern

- ```
    
  function add(x, y) { return x + y; }
  function sub(x, y) { return x y; }
  function mul(x, y) { return x * y; }
  function div(x, y) { return x / y; }
    
  var Command = function (execute, undo, value) {
      this.execute = execute;
      this.undo = undo;
      this.value = value;
   }
    
   var AddCommand = function (value) {
      return new Command(add, sub, value);
   };
    
   var SubCommand = function (value) {
      return new Command(sub, add, value);
   };
    
   var MulCommand = function (value) {
      return new Command(mul, div, value);
   };
    
   var DivCommand = function (value) {
      return new Command(div, mul, value);
   };
    
   var Calculator = function () {
      var current = 0;
      var commands = [];
    
      function action(command) {
          var name = command.execute.toString().substr(9, 3);
          return name.charAt(0).toUpperCase() + name.slice(1);
      }
    
      return {
          execute: function (command) {
              current = command.execute(current, command.value);
              commands.push(command);
              log.add(action(command) + ": " + command.value);
          },
    
          undo: function () {
              var command = commands.pop();
              current = command.undo(current, command.value);
              log.add("Undo " + action(command) + ": " + command.value);
          },
    
          getCurrentValue: function () {
              return current;
          }
      }
   }
    
   // log helper
    
   var log = (function () {
      var log = "";
    
      return {
          add: function (msg) { log += msg + "\n"; },
          show: function () { alert(log); log = ""; }
      }
   })();
    
   function run() {
      var calculator = new Calculator();
    
      // issue commands
    
      calculator.execute(new AddCommand(100));
      calculator.execute(new SubCommand(24));
      calculator.execute(new MulCommand(6));
      calculator.execute(new DivCommand(2));
    
      // reverse last two commands
    
      calculator.undo();
      calculator.undo();
    
      log.add("\nValue: " + calculator.getCurrentValue());
      log.show();
   }

  ```

  ​

In the example above we have a calculator with 4 basic operations: add, subtract, multiply and divide. Each operation is encapsulated by a Command object.

The Calculator maintains a stack of commands. Each new command is executed and pushed onto the stack. When an undo request arrives, it simply pops the last command from the stack and executes the reverse action.

JavaScript's function objects (and callbacks) are native command objects. They can be passed around like objects; in fact, they are true objects.

Diagram to explain how the command pattern works:

The objects participating in this pattern are:

Client: In the above code, the run () function references the Receiver object.

Receiver: In above code, the calculator knows how to carry out the operation associated with the command and maintains a history of executed commands.

Command: In the above code, the command maintains information about the action to be taken.

Invoker: In the above code the user pushes the buttons, asking it to carry out the request.

References

- https://code.tutsplus.com/tutorials/understanding-design-patterns-in-javascript--net-25930
- http://www.dofactory.com/javascript/design-patterns
- Addy Osmani (2012). Learning Javacript Design Pattern.