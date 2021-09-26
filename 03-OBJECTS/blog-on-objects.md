# Blog about object and its internal representation

## What is object in js?

Object is the building blocks of JavaScript. Object is a complex data type, not like the primitive data-types all store a single value each, but in object we can contain any combination of these primitive data-types, an object is a reference data type. Values are not directly stored to the variables, they got stored in a memory location which has been alloted for that variable, it is called as reference value. We might have seen this when we try to copy the objects, they key-value pairs are not actually get copied, instead the reference/memory location will be shared, so if any of the variables get modified the original object gets modified becuase both points to the same memory location.

Objects in javaScript may be defined as an unordered collection of related data, of primitive or reference types, in the form of key-value pairs. These keys can be variables or functions and are called properties and methods respectively

object has properties associated to it, the variable which is associated with that object is called as properties

> let person = {

    name: 'john'
    age: 24
    location: 'India'

}

Object can be accessed using dot notation

> console.log(person.name)

The object names and property names are case sensitive

Object can also be accessed using Bracket notation

> person['name'] = 'martin'
> console.log(person['name'])

Object is also called as Associated Arrays, because each property is associated with string value they can be used to access it, this bracket notation is helpful when there is dynamic object value is needed. Example in forms, if we are getting multiple inputs from the user and then creating an object out of it this notation is used for setting the values, dynamically set them when the keys changes

A function can also be a property in object they are called as methods,

> let person = {

    name: 'john'
    age: 24
    location: 'India'
    getInfo : function(){
        console.log(`My name is ${name} from ${location}`)
    }

}
person.getInfo()

Simplest and easiest way of creating an object is by using the object literal

ex:

> let person = {

    name: 'john'
    age: 24
    location: 'India'

}

Objects can be created using Object Constructor, with the help of 'new' keyword

ex:

> let person = new Object()
> person.firstName = 'jon'
> person.lastName = 'snow'
> person.age = 45
> console.log(person)

The Object Constructor creates a wrapper for the given value

Constructor is a function along with the help of new keyword, constructor functions are like templates for creating the objects, in another words it is defined as a set of properties and methods that are common to all the objects initialized using the constructor, with that we can have multiple objects

ex:

> function Rocket(name,manufacturer){

    this.name
    this.manufacturer

}
let rocket1 = new Rocket('Starship', 'SpaceX')
let rocket2 = new Rocket('New Shepard','Blue Orgin')

Another way of creating object is 'Object.create()' method

> Object.create(prototypeObject)

> let Rockets = {

    purpose: 'Inter Planetary Mission'

}
let rocket1 = Object.create(Rockets)
console.log(rocket1.purpose)

the 'Rockets' serves as the prototype for creating the object 'rocket1'

The objects which are created by using this method will inherit the properties and methods belongs to the prototype object, here there is no need to create a constructor function
