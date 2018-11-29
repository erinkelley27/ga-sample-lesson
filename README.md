# Prototypal Inheritance

## Learning Objectives

* Describe prototypal inheritance
* Describe a use-case for prototypal inheritance
* Explain the benefits of prototypal inheritance and its flexibility

## Prototype: The Hidden Property

You may know that objects can inherit from other objects. But did you know that all objects automatically have a hidden property called **prototypes**? Prototypes, whose values are either null or reference another object, are used to pass properties from a parent object to a child object.

## Relevant Review: Functions, Methods & Constructors

In simplified terms, a **function** is a block of code that takes an input, processes that input and then produces some form of output. A **method** is a function that is attached to an object. A **constructor** is a special method that will be invoked whenever we create a new instance of an object or class. All three are functions,but only a constructor can be passed down to another object throught prototypal inhertiance.

## Example

Let's take the example of renting a car and create an object called `car`, add properties for `engine`, `tires`, and a method for `drive`.

```
var car = {
    engine: true,
    tires: true,
    drive: function () {
        console.log('vroom vroom');
    }
};
```
Add this code snippet into the console and hit `return`. Type in `car.drive()`. What happens?

Next, let's create a new object called `jeep`. Here, we will add a few new properties that are unique to the `jeep` - `make`, `model`, and `year`.
```
var jeep = {
    make: "Jeep",
    model: "Wrangler",
    year: "2007"
};
```
Here comes the fun part: we are also going to use `__proto__` to set a prototype. We want to make `var car` the prototype for all of the other cars. When we do this, the properties and methods of `var car` will be passed down to `var jeep`.
```
var jeep = {
    make: "Jeep",
    model: "Wrangler",
    year: 2007,
    __proto__: car
};
```
Add this code snippet to the console and try entering `jeep.drive()`. What happens now? Try it with the other properties. Are you getting similar results?

## Object.create()

There's more than one way to put prototypal inheritance into action. An even simpler way to implement prototypal inheritance is to use the `Object.create()` function. Let's see how it works with our car example.
```
var car = {
    engine: true,
    tires: true,
    drive: function () {
        console.log('vroom vroom');
    }
};

var jeep = Object.create(car);

jeep.drive(); // 'vroom vroom'
```
You can populate the child object `var jeep` with unique properties.
```
jeep.make = "Jeep",
jeep.model = "Wrangler",
jeep.year = 2007
```
Keep in mind, the child object only has access to the properties of the parent object, through the **prototype chain** (the hidden link between the parent and child objects). It does not have these properties itself. 

Does `var car` contain the `engine` property? Does `var jeep`?

## Why is this useful for programmers?

**Simple |**
Prototypal inhertiance is easy to understand and easy to implement. Do you agree?

**Smaller, less redundant code |**
Prototypal inhertiance reduces the redundancy of code. Programmers do not need to code properties or methods that objects have in common over and over again because they can be passed from a parent to a child object. Basically, it helps keep your code DRY.

**Flexible |**
New properties and methods can be added to prototypes after they are created. These will be automatically passed down to all child objects of the prototype.

## Conclusion

So what is **prototypal inhertiance**? Simply put, it is when an object inherits directly from another object with the hidden property `prototype`.

## Additional Reading

* [Prototypal Inheritance in Javascript](https://medium.com/@kevincennis/prototypal-inheritance-781bccc97edb)
* [Inheritance and the Prototype Chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
* [Prototypal Inheritance](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
* [Master the JavaScript Interview: What’s the Difference Between Class & Prototypal Inheritance?](https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9)