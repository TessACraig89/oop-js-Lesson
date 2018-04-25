# Object Oriented Programming

| Objectives |
| :--- |
| Build practical and useful objects using Javascript constructors |
| Demonstrate a working knowledge of  object properties and methods  |

## What is Object Oriented Programming? 

OOP is a programming paradigm. It is a way of looking at programming. Some argue, it is a way of looking at the world! The principles behind OOP are that the world is a dynamic place of objects, or entities, that have properties, and functionality. These objects interface with other objects by passing messages to them in the form of calling a method, or getting or setting a property on them. 

This is in contrast to *functional programming*. We'll talk a little about that later today. 

Woah. 

## Ways to Create an object
For relatively straightforward and small objects, it is perfectly fine to declare them as a variable and define them as an *Object Literal*.
Here. I'll make you a flower using the *Literal* method:

```javascript
// Literal Object Definition
const flower = {
	color : "red",
	petals : 32,
	smellsPretty : true
}
``` 

## Constructors

Constructors allow us to create copies of Objects using the JavaScript `new` keyword. It's easy to remember because a Constructor constructs new objects. You've seen this a little bit before. We are now going to learn to create our own Constructors and how to make use of them. We will be using the ES5 `function` keyword here. We cannot use arrow function syntax for these for reasons explained below. 

Now lets make that flower!

 ```js
function Flower() {
    this.color = "red";
    this.petals = 32;
    this.smellsPretty= true;
 }

let myFlower = new Flower();

console.log(myFlower.color);
// "red"
 ```

The Literal definition of an object creates one single objected called flower.  There are no other flowers, just that one single object we created.  The constructor method is actually a function that creates a unique object every time it is called.  Below we will create a new variable `rose` that will use the constructor method to create a new object.

```javascript
var rose = new Flower();
```

Let us break down a couple concepts introduced with this new line of code:
- The capitalization of `Flower` lets everyone know that `Flower` is an object constructor.  Calling `Flower()` will return a `Flower` object.
- The `new`before our function call lets javascript know that we are creating a new object that will be independent of any other object.
- We call the flower function, which creates an object with the three pre-defined properties already made.  Our object is ready to go!

<img src = http://www.mzephotos.com/wallpapers/roses/red-rose-1024x768.jpg width = 75%>

Accessing the properties of our new `rose` object is the same as accessing our properties from data: we use dot or bracket notation.

```javascript
var color = rose.color // red
var petalCount = rose.petals // 32
var smellsNice = rose.smellsPretty //true
```

If we wanted to create yet ANOTHER flower, all we have to do is call our function just like we did above.  This time, lets make an object called `lily`.

```javascript
var lily = new Flower();
```

We can access the properties of `lily` in the same manner as we did with `rose`.

```javascript
var color = lily.color // red
var petalCount = lily.petals // 32
var smellsNice = lily.smellsPretty //true
```


&#x1F535; **Activity**
```
- In a JS file, create your own Flower constructor
- Add whatever properties you would like
- Create three instances of your Flower constructor using the 'new' keyword
- We named our flowers lily, and rose. You can use your favorite flower names
- Console.log one property from each flower instance
- Paste your code in the thread under these instructions
- 10 min
```  

## A side note on ES6 Classes

In **ES6** there is a new way to create **Constructors** using the `class` keyword. This was to clean up syntax a little bit and to follow the rest of the programming world's naming convention. To my knowledge *all other Object Oriented Porgramming Languages have classes*, and JavaScript didn't want to be left out. However, they didn't really add classes. They just started calling Constructors classes, and changed the syntax to look like this: 

```js
class Flower {
  constructor() {
    this.color = "red";
 	  this.petals = 32;
 	  this.smellsPretty= true;
  }
}
```

It looks nice, but the jury is out on whether or not this is a harmless detail, and the change is good, or this is a huge mistake. 

For that reason we will stick with the ES5 syntax and see how this plays out. That includes using the `function` keyword. 


## Changing an Object's properties

I don't know about you, but I generally like my Lillies yellow. I have also never heard of a lily with 32 petals, holy smokes!  Can we change our `lily` object to better reflect my perfect lily? You bet!

```javascript
// Changing object property values
lily.color = 'yellow';
lily.petals = 6;
```

That's more like it!  To change the value of the lily object properties. we simply access them with dot or bracket notation.  We then follow with an equals and a new appropriate value.  Couldn't be easier!

<img src = https://seniorhikerphotos.files.wordpress.com/2012/06/lilysarina12052301.jpg width = 75%>

## Object Methods
One of the most powerful features of Javascript Objects are Methods.  Methods are *"functions"* that are predefined and built into an object.  We all know and love the array Methods `forEach()`, `map()`, `filter()`, and `reduce()`; these are all Methods of the Array object.  We use arrays so much that Javascript automagically creates from an Array constructor without us having to instantiate them like we did above with the flowers.  Thanks, Javascript!

Lets make a simple method in the flower object that outputs to the console whenever we call it.


```javascript
function Flower(){
    this.color = "red";
    this.petals = 32;
    this.smellsPretty= true;
    // Demonstrates a simple method in an object
    this.sniff = function(){
        console.log("Sniff Sniff Sniff!");
    };
}
```

We now have a method inside our flower object called `sniff`.  When we call it, the console will display "Sniff Sniff Sniff!" as predicted.

Lets add another method that takes an argument and returns a response.

```javascript
function Flower(){
    this.color = "red";
    this.petals = 32;
    this.smellsPretty= true;
    // Demonstrates a simple method in an object
    this.sniff = function(){
        console.log("Sniff Sniff Sniff!");
    };
    // Demonstrates use of arguments with methods
    this.smellsGood = function(answer) {
    	if (answer) {
    		return 'This flower smells amazing!';
    	} else {
    		return 'What a noxious weed!';
    	}
    };
}
```
Methods can also access properties within the object with the `this` identifier then using dot or bracket notation.  Check out the method `describe()` below for an example.

```javascript
function Flower(){
    this.color = "red";
    this.petals = 32;
    this.smellsPretty= true;
    this.sniff = function(){
        console.log("Sniff Sniff Sniff!");
    };
    // Demonstrates use of arguments with methods
    this.smellsGood = function(answer) {
    	if (answer) {
    		return 'This flower smells amazing!';
    	} else {
    		return 'What a noxious weed!';
    	}
    };
    // Demonstrates use of local object variables
    this.describe = function(answer) {
        alert("This flower is " + this.color + ".");    
    }
}
```

&#x1F535; **Activity** She loves me, she loves me not...
```
- Create an object method for flower that will play the age old game ['He loves me, he loves me not...'](https://en.wikipedia.org/wiki/He_loves_me..._he_loves_me_not)
- Count down from the petal number down to 1
- Alternately display 'He loves me' or 'He loves me not' to the console for each petal count decrement.
- Display the final phrase with an exclamation; that's the end of the game!
- Paste your code in the thread under these instructions
- 10 minutes
```  


&#x1F535; **Activity**
```
- Create a new Constructor modeling any object of your choosing. We can model anything in code. A galaxy, a piece of lint, a lunch, anything!
- Add a function to that Constructor
- Paste your code in the thread under these instructions
- 6 minutes
```  

#### OOP is a big, complex topic. 

Great job getting through this lesson! This afternoon we'll see our tic tac toe game get refactored into OOP, and see what it does to our code. It should make it a little cleaner and more organized. But when it comes to large applications, it can be essential! However OOP is not the only game in town. The other paradigm in programming is *functional* programming. 

#### Functional Programming

Functional Programming is basically what we have been doing so far. However, as you may have heard, JavaScript is an Object Oriented *language* What this means is that the language itself is built using Object Oriented principles. Most importantly, it means that the language is build around the idea of creating *objects* that model *things* which have properties and functions, and *pass messages* to other objects. This also means that the language lends itself to Object Oriented code, and that some of JavaScripts most powerful features are best used in OOP. 

Some programming languages are *functional languages*, like Elm, Haskel, Erlang and Lisp. These languages are also very powerful programming languages and are designed with various uses, or sometimes for general use. These languages are built using functional paradigms, meaning it is not about objects that model things and pass messages to other objects. It is about *functions doing things in sequence*. This is cool and all, but outside of the scope of this course. 

#### Philosophy and OOP vs Functional Programming

<img src="https://fthmb.tqn.com/mG_3GKmgFZJDJ9Muswm9T3x2psY=/2121x1414/filters:fill(auto,1)/socrates-183232310-58cb18575f9b581d72aa8042.jpg" alt="socrates" width="500">

Some questions for your consideration: 

Is the world fundementally a world of independant, interconnected entities which have the ability to do things and interface with eachother? Or is it fundementally more like a machine driven from behind by *actions* like in functional programming?

If one of the above ways to look at the world were more true than the other, would that mean that that way of programming is better? Better for big things? Or certain things?

If programmers spend all day using one paradigm or another, could that effect the way that they view the world?

If *users* spend hours a day using a software that was built using one paradigm or the other, could *that* effect the way they view the world? 

If the software tools of the world were *all* built using one paradigm or another, would that effect the future of humanity?

![](https://media.giphy.com/media/kgEeS3motMqpW/giphy.gif)

This has been, some questions for your consideration. 
 
Further Suggested Reading:
- [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript)
- [MDN OOP for Beginners](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object-oriented_JS)
- [A 5 week part time online course in OOP JS](https://www.udacity.com/course/object-oriented-javascript--ud015)
- [Tutsplus](http://code.tutsplus.com/tutorials/the-basics-of-object-oriented-javascript--net-7670)
- [The best OOP educator out there is Sandi Metz](https://www.google.com/search?q=sandi+metz&rlz=1C5CHFA_enUS713US713&source=lnms&tbm=vid&sa=X&ved=0ahUKEwjVxOWh9JjYAhVpyVQKHSyOBQAQ_AUICigB&biw=1024&bih=581) She's a rubyist, so she talks about OOP in Ruby, but most of the concepts are the same as with JS, and they all are the same as with Python
