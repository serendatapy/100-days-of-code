# # This is a markdown Tutorial

### Insert as many hash as you need the headings

**I'm learning Markdown!!**

<!-- This is a way of taking notes like in HTML?-->

etc etc etc

And this way organise all the information

> this is a block quote of multi-line. It can go on and on as long as it's needed.

[Like this I can make a link to another site](fuzzynet.net)

[You can also add a title](http:fuzzy.net *It's my website I think*)

To make a table it's not so hard

| one   | two    | three      |
| ----- | ------ | ---------- |
| 1     | 2      | 3          |
| funny | things | are tables |

we can also make things *italic* like this and _this_ using underscore too

with **double asterix** things are _super_ _**strong**_!

you can do ~~strike through~~ style and make horizontal bars with hyphens

----

and this underlines

____

and also this stars

***

Make lists too

- one
- two

we can also use plus sign

+ like this
+ and this too

or also use star

* one
* two
* three

Most importantly we can include code blocks

```javascript
function add(num1,num2){
return num1+num2;
}
```

Typora just __works__ out of the **box!**

Now for an ordered list

1. thing
2. the other thing
3. that third one too
4. so there you go

Now let's make a task list

- [x] done
- [ ] not done

__*WOW*__ This works great!





# Codecademy Notes



## HTML 

The old convention was to put scripts right before the `</body>` tag to prevent the script from blocking the rest of the HTML content. Now, the convention is to put the script tag in the `<head>` element and to use the `defer` and `async` attributes.

### Defer & Async attribute

The *defer attribute* specifies scripts should be executed after the HTML file is completely parsed.

```html
<script src="example.js" defer></script> 
```

Specially useful when the script needs to interact with the DOM, and thus shouldn't be loaded before full page render. 



The *async attribute* specifies scripts should download in background as page continues to be rendered and execute as soon as it is ready to be loaded.

```html
<script src="example.js" async></script>
```

Useful when the script is independent of other scripts, and it doesn't matter when it loads. This is the OPTIMAL option for page load time.

### Forms

#### Input tag  & Form Validation

**Client side validation** can make sure data is _decent_ before being sent to the server. 

```html
<!--With / I indicate different options
Note 1: pattern attribute uses regex espression to set a format input
in this case we want only digits and numbers without special characters.
Note 2: you MUST include NAME attribute to store the input for sending, otherwise NO information will be sent. 
-->

<form action ="destination.html" method="POST">
    
	<label for="inputToValidate">Here you put text you want to be associated with your input field </label>
    
    <input id="inputToValidate" 
           name="groupname/variable name"
           type="text/number/radio/checkbox/password" 
           value = "a default value" 
           placeholder = "alternatively can use a placeholder to give hints to user" 
           min/minlength="5" 
           max/maxlength="150"
           pattern="[a-zA-Z0-9]+"
           required>
    <input type="submit" value="Submit">
</form>

```


### Odd form types

#### Data-lists

```html
<form action="/quiz.html" method="POST">
  <label for="choice">What's wrong with this code?</label>
  <input id="choice" type="text" name="find-the-answer" list="menu-options">
  <datalist id="menu-options">
      <option value="one"></option>
      <option value="two"></option>
      <option value="three"></option>
  </datalist>
</form>
```

#### Drop-down Menu

```html
<section class="bun-type">
          <label for="bun">What type of bun would you like?</label>
          <select name="bun" id="bun">
            <option value="sesame">Sesame</option>
            <option value="potatoe">Potato</option>
            <option value="pretzel">Pretzel</option>
          </select>
        </section>
```



## CSS

### Specificity - CSS Hierarchy

Best practice is to apply CSS with lowest degree of specificity possible, so that if something needs to be re-styled, it can be done easily.
Lowest to Highest

1. Tag style
2. Class Style
3. h1.special
4. .special h1
5. ID Style -> this overrides all previous styles, use appropriately only when necessary.
6. Inline styles
7. !important -> never use this unless there is no other way. Bad practice.

Pseudo classes count as a class, so be careful, as an ID could override the hover effect!



# Javascript



## Array Methods

### SPLICE() Add Remove Replace (MUTATING)

```javascript
// Remove 0 (zero) elements before index 2, and insert "drum" 
let myFish = ['angel', 'clown', 'mandarin', 'sturgeon']
let removed = myFish.splice(2, 0, 'drum')
// myFish is ["angel", "clown", "drum", "mandarin", "sturgeon"] 
// removed is [], no elements removed

// Remove 1 element at index 3 
let myFish = ['angel', 'clown', 'drum', 'mandarin', 'sturgeon']
let removed = myFish.splice(3, 1)
// myFish is ["angel", "clown", "drum", "sturgeon"]
// removed is ["mandarin"] 

// Remove 1 element at index 2, and insert "trumpet" 
let myFish = ['angel', 'clown', 'drum', 'sturgeon']
let removed = myFish.splice(2, 1, 'trumpet')
// myFish is ["angel", "clown", "trumpet", "sturgeon"]
// removed is ["drum"]

// Rm 2 elements from index 0, and insert "parrot", "anemone" and "blue" 
let myFish = ['angel', 'clown', 'trumpet', 'sturgeon']
let removed = myFish.splice(0, 2, 'parrot', 'anemone', 'blue')
// myFish is ["parrot", "anemone", "blue", "trumpet", "sturgeon"] 
// removed is ["angel", "clown"]

// Remove 2 elements from index 2 
let myFish = ['parrot', 'anemone', 'blue', 'trumpet', 'sturgeon']
let removed = myFish.splice(2, 2)
// myFish is ["parrot", "anemone", "sturgeon"] 
// removed is ["blue", "trumpet"]

// Remove 1 element from index -2 
let myFish = ['angel', 'clown', 'mandarin', 'sturgeon']
let removed = myFish.splice(-2, 1)
// myFish is ["angel", "clown", "sturgeon"] 
// removed is ["mandarin"]

// Remove all elements after index 2 (incl.) 
let myFish = ['angel', 'clown', 'mandarin', 'sturgeon']
let removed = myFish.splice(2)
// myFish is ["angel", "clown"]
// removed is ["mandarin", "sturgeon"]
```

### For Each

When passing a function as an argument, pass the function directly, and where the function is defined, it can take the values of a usual for each function. ForEach returns undefined by default.

```javascript
const veggies = ['broccoli', 'spinach', 'cauliflower', 'broccoflower'];

const politelyDecline = (veg) => {
      console.log('No ' + veg + ' please. I will have pizza with extra cheese.');
}

// Write your code here:
function declineEverything(stringArr) {
  stringArr.forEach(politelyDecline);
  }
```

### map

Use map when you need a NEW array RETURNED, unlike forEach that is used when you want to DO something with existing values.

```javascript
// Write your code here:

function shoutGreetings(stringArr) {
  return stringArr.map(word => `${word}!`.toUpperCase());
}

// Feel free to uncomment out the code below to test your function!
const greetings = ['hello', 'hi', 'heya', 'oi', 'hey', 'yo'];

console.log(shoutGreetings(greetings))
// Should print [ 'HELLO!', 'HI!', 'HEYA!', 'OI!', 'HEY!', 'YO!' ]
```

### sort

The order is created by the condition, in this case is descending

```javascript
// EXAMPLE 1

function sortYears(yearsArr) {
  return yearsArr.sort((a,b) => b - a); //compares numbers
}

// Feel free to uncomment the below code to test your function:
const years = [1970, 1999, 1951, 1982, 1963, 2011, 2018, 1922]

console.log(sortYears(years))
// Should print [ 2018, 2011, 1999, 1982, 1970, 1963, 1951, 1922 ]

// EXAMPLE 2
const speciesArray = [ {speciesName:'shark', numTeeth:50}, {speciesName:'dog', numTeeth:42}, {speciesName:'alligator', numTeeth:80}, {speciesName:'human', numTeeth:32}];

function sortSpeciesByTeeth(speciesArrOfObj) {
  let sortedInAscend = speciesArrOfObj.sort((animalObjA,animalObjB) => {
    return animalObjA.numTeeth - animalObjB.numTeeth;
  })
  return sortedInAscend;
}

// FUNCTION DESTRUCTURED
function sortSpeciesByTeeth(speciesArrOfObj) {
  return speciesArrOfObj.sort((animalObjA,animalObjB) => animalObjA.numTeeth - animalObjB.numTeeth)
}


console.log(sortSpeciesByTeeth(speciesArray))

/* Should print [ { speciesName: 'human', numTeeth: 32 },
  { speciesName: 'dog', numTeeth: 42 },
  { speciesName: 'shark', numTeeth: 50 },
  { speciesName: 'alligator', numTeeth: 80 } ]
*/
```

### Filter

All elements that pass a condition are RETURNED as a NEW array. If none pass the condition an EMPTY array is returned. 

```javascript
// Write your code here:
function justCoolStuff(stringArr1,stringArr2) {
  let inCommonArr = stringArr1.filter((word) => {
    if(stringArr2.indexOf(word) > -1) return word; 
  });
  return inCommonArr;
}

// Feel free to uncomment the code below to test your function

const coolStuff = ['gameboys', 'skateboards', 'backwards hats', 'fruit-by-the-foot', 'pogs', 'my room', 'temporary tattoos'];

const myStuff = [ 'rules', 'fruit-by-the-foot', 'wedgies', 'sweaters', 'skateboards', 'family-night', 'my room', 'braces', 'the information superhighway']; 

console.log(justCoolStuff(myStuff, coolStuff))
// Should print [ 'fruit-by-the-foot', 'skateboards', 'my room' ]
```

### Every

Returns boolean to indicate if all elements pass the test

```javascript
function isTheDinnerVegan(foodArrOfObj) {
 return foodArrOfObj.every(foodObject => {
   return foodObject.source === 'plant';
 })
}

DESTRUCTURED
function isTheDinnerVegan(foodArrOfObj) {
 return foodArrOfObj.every(foodObject => foodObject.source === 'plant')
}
```

### indexOf vs findIndex

```javascript
//indexOf is appropiate for finding simple primitive types
function findMyKeys(stringArr) {
  return stringArr.indexOf('keys');
}


//when conditions are more complex findIndex() gives more flexibility
function findMyKeys(stringArr) {
  return stringArr.findIndex(element => element === 'keys');
}

const randomStuff = ['credit card', 'screwdriver', 'receipt', 'gum', 'keys', 'used gum', 'plastic spoon'];

console.log(findMyKeys(randomStuff))
// Should print 4
```







## Objects

#### Bracket Notation [ ]

IMPORTANT NOTE: when using bracket notation, it SUBSTITUTES the DOT notation!

We *must* use bracket notation when accessing keys that have numbers,  spaces, or special characters in them. Without bracket notation in these situations, our code would throw an error.

```javascript
let spaceship = {
  'Fuel Type': 'Turbo Fuel',
  'Active Duty': true,
  homePlanet: 'Earth',
  numCrew: 5
};
spaceship['Active Duty'];   // Returns true
spaceship['Fuel Type'];   // Returns  'Turbo Fuel'
spaceship['numCrew'];   // Returns 5
spaceship['!!!!!!!!!!!!!!!'];   // Returns undefined
```

With bracket notation you can also use a variable inside the brackets to select the keys of an object. This can be especially helpful when  working with functions:

```javascript
let spaceship = {
  'Fuel Type' : 'Turbo Fuel',
  'Active Mission' : true,
  homePlanet : 'Earth', 
  numCrew: 5,
  'Secret Mission' : 'Discover life outside of Earth.',
  mission: 'Explore the universe' 
 };

let propName =  'Active Mission';
console.log(spaceship[propName]);
/*DOT notation here gives undefined! Because the computer would look for a property with that name, rather than with it's value as variable*/
//Assigning new values
spaceship.color = 'glorious gold';
spaceship['numEngines'] = 8;
//Could also delete
delete spaceship['Secret Mission'];
delete spaceship.mission; 

```

#### Methods

```javascript
let retreatMessage = 'We no longer wish to conquer your planet. It is full of dogs, which we do not care for.';

// Write your code below
const alienShip ={
  retreat : function() { //using anonymous function as method
    console.log(retreatMessage)
  },
  takeOff () { //with ES6 shorthand
    console.log('Spim... Borp... Glix... Blastoff!')
  }
};

alienShip.retreat();
alienShip.takeOff();
```

#### Nested Objects

```javascript
const spaceship = {
     telescope: {
        yearBuilt: 2018,
        model: '91031-XLT',
        focalLength: 2032 
     },//end telescope
     crew: {
        captain: { 
            name: 'Sandra', 
            degree: 'Computer Engineering', 
            encourageTeam() { console.log('We got this!') } 
         }
     },//end crew
     engine: {
        model: 'Nimbus2000'
     },//end engine
     nanoelectronics: {
         computer: {
            terabytes: 100,
            monitors: 'HD'
         },
        'back-up': {
           battery: 'Lithium',
           terabytes: 50
         }
     }//end nanoelectronics
}; 
//access nested objects
spaceship.nanoelectronics['back-up'].battery; // Returns 'Lithium'
```

#### Pass By Reference !! WEIRD PART

```javascript
/*FUNCTION THAT CHANGES OBJECT PROPERTIES WORK*/

const spaceship = {
  homePlanet : 'Earth',
  color : 'silver'
};

let paintIt = obj => {
  obj.color = 'glorious gold'
};

paintIt(spaceship);

spaceship.color // Returns 'glorious gold'

/*-----------------BUT-----------------*/
/*FUNCTION THAT REASSIGNS OBJECT DOESN'T WORK*/

let spaceship = {
  homePlanet : 'Earth',
  color : 'red'
};
let tryReassignment = obj => {
  obj = {
    identified : false, 
    'transport type' : 'flying'
  }
  console.log(obj) // Prints {'identified': false, 'transport type': 'flying'}

};
tryReassignment(spaceship) // The attempt at reassignment does not work.
spaceship // Still returns {homePlanet : 'Earth', color : 'red'};

/*WHY: An object passed as a parameter, passes only the memory location, and NOT the variable itself. In the reassign function, obj is a variable in itself! So it has not connection with the original variable*/

//A Regular reassignment works however (because it's not a const!)
spaceship = {
  identified : false, 
  'transport type': 'flying'
}; // Regular reassignment still works.

```

#### Looping through objects (For...in)

```javascript
let spaceship = {
    crew: {
    captain: { 
        name: 'Lily', 
        degree: 'Computer Engineering', 
        cheerTeam() { console.log('You got this!') } 
        },
    'chief officer': { 
        name: 'Dan', 
        degree: 'Aerospace Engineering', 
        agree() { console.log('I agree, captain!') } 
        },
    medic: { 
        name: 'Clementine', 
        degree: 'Physics', 
        announce() { console.log(`Jets on!`) } },
    translator: {
        name: 'Shauna', 
        degree: 'Conservation Science', 
        powerFuel() { console.log('The tank is full!') } 
        }
    }
}; 
// for...in
for (let crewMember in spaceship.crew) {
  console.log(`${crewMember}: ${spaceship.crew[crewMember].name}`)
};
//Note: Usage of bracket notation to pass the variable crewMember
```

### THIS 

Watch out for different kinds of functions

```javascript
/*THIS refers to CALLING OBJECT, now it's robot*/
const robot = {
  model: '1E78V2',
  energyLevel: 100,
  provideInfo() { //USE OF SHORTHAND FUNCTION
    return `I am ${this.model} and my current energy level is ${this.energyLevel}`;
  }
};
console.log(robot.provideInfo()); //I am 1E78V2 and my current energy level is 100


```

#### Arrow Functions WEIRD PART

```javascript
const goat = {
  dietType: 'herbivore',
  makeSound() {
    console.log('baaa');
  },
  diet: () => {
    console.log(this.dietType);
  }
};

goat.diet(); // Prints undefined

/*Arrow functions inherently bind, or tie, an already defined this value to the function itself that is NOT the calling object. In the code snippet above, the value of this is the global object, or an object that exists in the global scope, which doesn’t have a dietType property and therefore returns undefined. */
```

The key takeaway from the example above is to *avoid* using arrow functions when using `this` in a method! 

### Privacy Getters and Setters

Although they LOOK like methods, they are NOT METHODS in they way they are INVOKED LIKE PROPERTIES!

```javascript
/*Getters can do more than just retrieve information*/
const person = {
  _firstName: 'John',
  _lastName: 'Doe',
  get fullName() { //GETTER FUNCTION
    if (this._firstName && this._lastName){
      return `${this._firstName} ${this._lastName}`;
    } else {
      return 'Missing a first name or a last name.';
    }
  }
}

// To call the getter method: 
person.fullName; // 'John Doe'
//Syntatically it looks like we're accessing a property! 
```

* Can do what functions do
* Makes code more understandable
* Mustn't have the same name as another property (infinite call stack error)
* properties that shouldn't be accessed directly have an underscore before it

```javascript
/*Setters reassing values within objects*/
const person = {
  _age: 37,
  set age(newAge){
    if (typeof newAge === 'number'){
      this._age = newAge;
    } else {
      console.log('You must assign a number to age');
    }
  }
};

person.age = 40;
console.log(person._age); // Logs: 40
person.age = '40'; // Logs: You must assign a number to age
```

* Can do what functions do
* Let's us perform checks before reassigning
* Let's us give feedback to the user/system
* Syntactically it looks like we're assigning a property



### Factory Functions 

We can create multiple objects quickly and can take parameters to allow customisation.

```javascript
const monsterFactory = (name, age, energySource, catchPhrase) => {
  return { 
    name: name,
    age: age, 
    energySource: energySource,
    scare() {
      console.log(catchPhrase);
    } 
  }
};

const ghost = monsterFactory('Ghouly', 251, 'ectoplasm', 'BOO!');
ghost.scare(); // 'BOO!'
const yeti = monsterFactory('White Big Foot', 100, 'rage', 'Arr!');
yeti.scare(); // 'Arr!'


//COMPLETE FACTORY FUNCTION
unction dogFactory(name,breed,weight){
  return {
    _name:name,
    _breed:breed,
    _weight:weight,

    set name (newName) {
      this._name = newName;
    },
    set breed (newBreed) {
      this._breed = newBreed;
    },
    set weight (newWeight) {
      this._weight = newWeight;
    },

    get name () {
      return this._name
    },
    get breed () {
      return this._breed
    },
    get weight () {
      return this._weight
    },
    bark () {
      return 'ruff! ruff!'
    },
    eatTooManyTreats () {
      this.weight++;
    }
  } //end obj
}


console.log(dogFactory('Joe', 'Pug', 27))
// Should return { name: 'Joe', breed: 'Pug', weight: 27 }

let snoopy = dogFactory('Snoopy','Cartoon',20);
console.log(snoopy); // prints object
console.log(snoopy.bark()); //prints noise
snoopy.eatTooManyTreats(); // increments weight
console.log(snoopy.weight); // 21
```

## Destructuring ES6

### Destructuring Objects

#### Obtaining values from objects

Note: **variable names** must be the **same** as **key names** to work

```javascript
let personOne = {
    name: 'kyle',
    age: 24,
    address: {
        city: 'Somewhere',
        state: 'One of them'
    }
}

let personTwo = {
    name: 'Sally',
    age: 32,
    address: {
        city: 'Nowhere',
        state: 'None of them'
    }
}

let {name,age} = PersonOne;
/* is equivalent to
let name = PersonOne.name
let age = PersonOne.age
*/
let {name: firstName = 'Unnamed', age: oldAge, ...rest} = PersonTwo;
/* is equivalent to
let firstName = PersonTwo.name  (will give 'Unnamed' default value if key not present)
let oldAge = PersonTwo.age
let rest = //everything else inside object as an object
*/
let {name: myName, age: myAge, address: { city } } = PersonTwo;
/* is equivalent to
let myName = PersonTwo.name 
let myAge = PersonTwo.age
let address = PersonTwo.address.city
*/


```

#### Combine Objects

```javascript
let personOne = {
    age: 24,
    address: {
        city: 'Somewhere',
    }
}

let personTwo = {
    name: 'Sally',
    age: 32,
    address: {
        state: 'None of them'
    }
}

let personThree = {...personOne, ...personTwo}
/*This is equivalent to
getting all the information from personOne into personThree
getting all the information from personTwo into personThree
where there were already existing keys, overwrite.

personThree = {
let personOne = {
    name: 'Sally',
    age: 32,
    address: {
        city: 'Somewhere',
        state: 'None of them'
    }
}
*/
```

#### Using objects destructured as arguments

```javascript
let personOne = {
    name: 'kyle',
    age: 24,
    address: {
        city: 'Somewhere',
        state: 'One of them'
    }
}

function printUser({name,age,favoriteFood = 'Watermelon'}){
    console.log(`Name is: ${name}. Age is ${age}. Food is ${favoriteFood}`)
}

/* is equivalent and better than:
function printUser(user){
    console.log(`Name is: ${user.name}. Age is ${user.age}. Food is user.favoriteFood`)
}
*/
printUser(personOne)
```

#### Property Value Shorthand ES6 

```javascript
/*When the property name is the same as the value, we can...*/
const monsterFactory = (name, age, energySource, catchPhrase) => {
  return { 
    name,
    age, 
    energySource,
    scare() {
      console.log(catchPhrase);
    } 
  }
};
```

#### destructured assignment

```javascript
const vampire = {
  name: 'Dracula',
  residence: 'Transylvania',
  preferences: {
    day: 'stay inside',
    night: 'satisfy appetite'
  }
};

const residence = vampire.residence; 
console.log(residence); // Prints 'Transylvania'

/*DESTRUCTURED*/
//variable must have name of object's key and wrapped in {}
const { residence } = vampire; 
console.log(residence); // Prints 'Transylvania'
```

### Destructuring Arrays

#### obtaining values from arrays

```java
const alphabet = ['A','B','C','D','E','F'];
const numbers = ['1','2','3','4','5','6'];

let [x,y] = alphabet;
/*
let x = alphabet[0]; // 'A'
let y = alphabet[1]; // 'B'
*/
let [x,,,z,...rest] = alphabet;
/*
let x = alphabet[0]; // 'A'
let z = alphabet[3]; // 'D'
let rest = [alphabet[4],alphabet[5]] // [ 'E' , 'F' ]
*/
```

#### Destructured arrays and functions

```javascript
function sumAndMultiply(a, b){ 
return [a+b,a*b]
}

let [sum, multiply, division = 'No Division'] = sumAndMultiply(2,3)
/*
the return value is an array with 2 numbers, these are divided into
SUM and MULTIPLY let variables. 
DIVISION uses a default value, if third argument is not returned.
*/
```



### Classes

There are a lot of *similarities* between Classes & Factory Functions and Objects, but also some **important Differences** 

* Classes are created with the keyword **'class'** and are not variables!

* Classes have a **constructor** and need the keyword **'new'** to instantiate!

* Inside the constructor we use **'='** RATHER than **':'** as you would in objects, and also the keyword **this**

* Classes can use the keyword **super** to inherit constructor from a parent class it **extends**

* When the class **extends** another, it inherits all it's properties and methods

* Properties and Methods inside the Class have **';'** instead of a **','** or often nothing at all!

* Classes can have **Static** Methods, that can only be called from the class and not from the instance

  

```javascript
/*An Important difference however is the CONSTRUCTOR METHOD called every time an object is instantiated*/

class Dog {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }
  get behavior() {
    return this._behavior;
  }   

  incrementBehavior() {
    this._behavior ++;
  }
}
/*Another Important difference, the NEW keyword*/
const halley = new Dog('Halley');
console.log(halley.name);
console.log(halley.behaviour);
halley.incrementBehavior();
console.log(halley.name);
console.log(halley.behavior);
```

#### Instance

 An *instance* is an object that contains the property names and methods of a class, but with unique property values. 

```javascript
class Dog {
  constructor(name) {
    this.name = name;
    this.behavior = 0;
  } 
}
/*The new keyword calls the constructor which returns the new instance*/
const halley = new Dog('Halley'); // Create new Dog instance
console.log(halley.name); // Log the name value saved to halley
// Output: 'Halley'
```

Class method and getter syntax is the same as it is for objects **except you can not include commas between methods**.

#### Inheritance

``` javascript
/*The Cat class, shares some properties and methods with the dog class*/
class Cat {
  constructor(name, usesLitter) {
    this._name = name;
    this._usesLitter = usesLitter;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get usesLitter() {
    return this._usesLitter;
  }

  get behavior() {
    return this._behavior;
  }  

  incrementBehavior() {
    this._behavior++;
  }
}

/*When multiple classes share properties, they could be joined together into a super class*/

class Animal {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }

  get behavior() {
    return this._behavior;
  }   

  incrementBehavior() {
    this._behavior++;
  }
} 

/*Once the super class is in place, the sub-classes will look like this*/
//EXTENDS SUPERCLASS - makes methods from super available in sub
class Cat extends Animal {
  constructor(name, usesLitter) {
    super(name); 
      /*called on the first like of constructor,
      Super keyword runs super's constructor inside subclass
      then further properties, like usesLitter can be added*/
    this._usesLitter = usesLitter; //this is a new property
  }
   get usesLitter() {
    return this._usesLitter;
  }
}

clas Dog extends Animal {
    constructor(name) {
        super(name);
    }
}

const bryceCat = new Cat('Bryce', false); 
console.log(bryceCat.name); // output: Bryce using SUPER's GETTER
```

#### Static Methods

Static methods can be called directly from the class but not from it's instances. 

```javascript
class Animal {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  static generateName() {
    const names = ['Angel', 'Spike', 'Buffy', 'Willow', 'Tara'];
    const randomNumber = Math.floor(Math.random()*5);
    return names[randomNumber];
  }
} 

console.log(Animal.generateName()); // returns a name


```

## The DOM

The DOM is a virtual object representation of the html document, that allows access to javascript for manipulation. 

```javascript
document.body.innerHTML = 'The cat loves the dog.';
```

#### innerHTML

note: innerHTML replaces content, so in the example below, all other content present in body will dissapear and be replaced by the sole h2 tag

```javascript
//other than above, it can also be used to add more html
document.body.innerHTML = '<h2>This is a heading</h2>';
```

#### querySelector - CSS

You can also use other CSS selectors such as an element’s `.` class or its `#` ID.

```javascript
document.querySelector('p');
```

#### getElementById

```javascript
document.getElementById('bio').innerHTML = 'The description';
```

#### Access Styles CSS

```javascript
//When accessing styles through DOM, use CamelCase instead of : hyphens

let blueElement = document.querySelector('.blue');
blueElement.style.backgroundColor = 'blue';

OR

document.querySelector('.blue').style.fontFamily = 'Roboto';

/*--------------------------------------*/
let bodyStyle = document.querySelector('body');
bodyStyle.style.backgroundColor = '#201F2E';

document.querySelector('body').style.backgroundColor = '#201F2E';
```

#### createElement(tagName) & appendChild()

```javascript
let paragraph = document.createElement('p');

paragraph.id = 'info'; 

paragraph.innerHTML = 'The text inside the paragraph';

document.body.appendChild(paragraph);

/*----------------Example 2-------------*/
let newDestination = document.createElement('li');
newDestination.id = 'oaxaca';
newDestination.innerHTML = 'Oaxaca, Mexico';
document.body.querySelector('#more-destinations').appendChild(newDestination);

/*How to implement above using getElementById instead of querySelector*/
```

#### RemoveChild()

```javascript
let v = document.body.querySelector('#oaxaca');
document.body.querySelector('#more-destinations').removeChild(v);

/*Alternatively Elements could also be hidden*/
document.getElementById('#oaxaca').hidden = true;
```

#### onclick()

```javascript
let element = document.querySelector("button");

element.onclick = turnButtonRed;

function turnButtonRed (){
  element.style.backgroundColor = 'red';
  element.style.color = 'white';
  element.innerHTML = 'Red Button'
}
```

#### .parentNode & .children properties

Returns a list of elements or null. 

```javascript
let first = document.body.firstChild;
first.innerHTML = 'I am the child!'

first.parentNode.innerHTML = 'I am the parent and my inner HTML has been replaced!'

/*The first command could change a h1 for example, however we won't see it because the last command wipes out everything, leaving only the text we entered last*/
```

#### event handler registration

When we add a function to the eventTarget, we create a property for it. 

Note: this allows adding just one handler per object.

```javascript
let eventTarget = document.getElementById('targetElement');

//create an event handler property (on-eventType)
eventTarget.onclick = function() {
    //This is the eventHandler function assigned to the property  
    // this block of code will run
}
/*This can also be done inline to a html element, but it's bad practice*/

/*----------Example 2---------------*/
let readMore = document.getElementById('read-more');

let moreInfo = document.getElementById('more-info');

// Write your code here:
readMore.onclick = function (){
  moreInfo.style.display = 'block';
}

/*BEST PRACTICE TO NAME EVENT HANDLER FUNCTIONS*/
```

#### addEventListener()

addEventListener(eventType, eventHandlerFunction)

```javascript
eventTarget.addEventListener('click', eventHandlerFunction);
/*EXAMPLE*/

// Add the code you want to test below:
let view = document.getElementById('view-button');
let close = document.getElementById('close-button');
let codey = document.getElementById('codey');

let open = function() {
  codey.style.display = 'block';
  close.style.display = 'block';
};

let hide = function() {
  codey.style.display = 'none';
  close.style.display = 'none';
};

let textChange = function () {
  view.innerHTML = 'Hello World!';
}
let textReturn = function () {
  view.innerHTML = 'View';
}

view.onclick = open; //OR view.addEventListener('click',open);
view.addEventListener('click',textChange);
close.addEventListener('click',textReturn);
close.onclick = hide;
```

This allows you to add multiple event handlers to a single element without overwriting the others!

#### removeEventListener()

removeEventListener(eventType, eventHandlerFunction)

```javascript
/*This code operates a door opening with lock unlock mechanism*/
let door = document.getElementById('door');
let unlock = document.getElementById('unlock');
let lock = document.getElementById('lock');
let sign = document.getElementById('sign');
let cafeImage = document.getElementById('image');

cafeImage.hidden = true;

let openDoor = function() {
  door.hidden = true;
  cafeImage.hidden = false;
}

let closeDoor = function(){
  door.hidden = false;
  cafeImage.hidden = true;
}

unlock.onclick = function() {
  sign.innerHTML = 'OPEN';
  unlock.style.backgroundColor = '#6400e4';
  lock.style.backgroundColor = 'lightgray';
}

lock.onclick = function() {
  sign.innerHTML = 'CLOSED';
  lock.style.backgroundColor = '#6400e4';
  unlock.style.backgroundColor = 'lightgray';
}

unlock.addEventListener('click', function(){
  door.addEventListener('click', openDoor);
  cafeImage.addEventListener('click', closeDoor);
})

// Write your code here
lock.addEventListener('click',function(){
  door.removeEventListener('click',openDoor);
});
```



#### Event Object Properties ( e )

JavaScript stores events as *event objects* with their related data and functionality as properties and methods. 

- the `.target` property to access the element that triggered the event.
- the `.type` property to access the name of the event.
- the `.timeStamp` property to access the number of milliseconds that passed since the document loaded and the event was triggered.

```javascript
let social = document.getElementById('social-media');
let share = document.getElementById('share-button');
let text = document.getElementById('text');

// Write your code below
let sharePhoto = function(event) {
  event.target.style.display = 'none';
  let timeS = event.target.timeStamp;
  text.innerHTML = `${timeS}`;
}

share.addEventListener('click',sharePhoto);
```

[MDN Events Reference](https://developer.mozilla.org/en-US/docs/Web/Events) 

#### Other Event Types - Examples

```javascript
//Logic for 2 color picker buttons
// This variable stores the "Pick a Color" button
let button = document.getElementById('color-button');

// This variable stores the "Mystery Color" button
let mysteryButton = document.getElementById('next-button');

// This random number function that will creates color codes for the randomColor variable
function rgb(num) {
  return Math.floor(Math.random() * num);
}

// Write your code below
let colorChange = function (event) {
  let randomColor = 'rgb(' + rgb(255) + ',' + rgb(255) + ',' + rgb(255) + ')';
  event.target.style.backgroundColor = randomColor;  
}

button.onclick = colorChange;
mysteryButton.onwheel = colorChange;
```

#### Mouse Events

```javascript
// These variables store the boxes on the side
let itemOne = document.getElementById('list-item-one');
let itemTwo = document.getElementById('list-item-two');
let itemThree = document.getElementById('list-item-three');
let itemFour = document.getElementById('list-item-four');
let itemFive = document.getElementById('list-item-five');
let resetButton = document.getElementById('reset-button');

// This function programs the "Reset" button to return the boxes to their default styles
let reset = function() {
  itemOne.style.width = ''
  itemTwo .style.backgroundColor = ''
  itemThree.innerHTML = 'The mouse must leave the box to change the text'
  itemFive.style.display = "none"
};
resetButton.onclick = reset;

// Write code for the first list item
itemOne.onmouseover = function(){
  itemOne.style.width = '500px';
};

// Write code for the second list item
itemTwo.onmouseup = function(){
  itemTwo.style.backgroundColor = 'grey';
}

// Write code for the third list item
itemThree.onmouseout = function(){
  itemThree.innerHTML = 'The mouse has left the element.';
}

// Write code for the fourth list item
itemFour.onmousedown = function(){
  itemFive.style.display = 'block';
}
```

#### Keyboard Events

```javascript
/*Simulate the dribbling of a ball*/
let ball = document.getElementById('float-circle');

// Write your code below
function up() {
  ball.style.bottom = '250px';
}

function down() {
  ball.style.bottom = '50px';
}

document.onkeydown = up;
document.onkeyup = down;
```



## Modules (node.js & ES6)

Generally speaking ES6 syntax is used for frontend development and node for backend.

### Export

```javascript
//in menu.js
//Module Definition
let Menu = {};
Menu.specialty = "Roasted Beet Burger with Mint Sauce";

//exports module
module.exports = Menu; 

/*Here 'module' is a variable and 'exports' exposes the object
You could also do a direct assignment */

module.exports.Menu = {
     speciality : "Roasted Beet Burger with Mint Sauce"
}
/*-----------------------------EXPORT B----------------------*/
module.exports = {
  specialty: "Roasted Beet Burger with Mint Sauce",
  getSpecialty: function() {
    return this.specialty;
  } 
};


//you can assign module.exports Multiple Objects to be exported

let MainObject = {};

MainObject.objToExport = {
  propOne: 1,
  propTwo: 2
};

MainObject.anotherObjToExport = {
  anotherProp: 3,
  andAnother: 4
};

module.exports = MainObject;

//OR

module.exports.objToExport = {
  propOne: 1,
  propTwo: 2
};

module.exports.anotherObjToExport = {
  anotherProp: 3,
  andAnother: 4
};

//OR

module.exports = {
  objToExport: {
    propOne: 1,
    propTwo: 2
  },
  anotherObjToExport: {
    anotherProp: 3,
    andAnother: 4
  }
};

```

This is for NODE.JS

1. Create an object to represent the module. 
2. Add properties or methods to the module object.
3. Export the module with `module.exports`.

Instead for ES6 (not supported in Node environment)

METHOD 1

```javascript
let Menu = {};

export default Menu;
/*export can export Objects, Functions and Primitive Data*/
```

METHOD 2 (named)

```javascript
let specialty = '';
function isVegetarian() {
}; 
function isLowSodium() {
}; 

export { specialty, isVegetarian };

/*Alternatively they can be exported directly*/

export let specialty = '';
export function isVegetarian() {
}; 
function isLowSodium() {
};  
//this would eliminate the need of the final statement
//THIS DOES NOT IMPACT HOW WE IMPORT

//Extention - we can also change variable name with the AS keyword
let specialty = '';
let isVegetarian = function() {}; 
let isLowSodium = function() {}; 

export { specialty as chefsSpecial, isVegetarian as isVeg, isLowSodium };
/*In this case when we import, we need to import the alias, however for isLowSodium, which wasn't aliased, we can do the alias when we import*/
```



Notice that, when we use named  exports, we are not setting the properties on an object. Each export is  stored in its own variable.

`specialty` is a string object, while `isVegetarian` and `isLowSodium` are objects in the form of functions. Recall that in JavaScript, every function is in fact a function object. 

`export { specialty, isVegetarian };` exports objects by their variable names. Notice the keyword `export` is the prefix. 

`specialty` and `isVegetarian` are exported, while `isLowSodium` is not exported, since it is not specified in the export syntax

### Import

Using **require(filePath)** we can import a module. This function loads a module. The .js extension is optional, it will be assumed if not included.

``` javascript
// in order.js
const Menu = require('./menu.js');
/*This makes the entire behaviour of Menu available here.
Note: we could give a different name to the variable if we wanted
such as menuItems*/

function placeOrder() {
  console.log('My order is: ' + Menu.specialty); //access module
}

placeOrder();
/*---------------------IMPORT B-----------------------*/

const Menu = require('./menu.js');
console.log(Menu.getSpecialty());
```

This is for NODE.JS

1. Import the module with `require()` and assign it to a local variable.
2. Use the module and its properties within a program. 

Instead for ES6

METHOD 1

1. The `import` keyword begins the statement.
2. The keyword `Menu` here specifies the name of the variable to store the default export in.
3. `from` specifies where to load the module from. 
4. `'./menu'` is the name of the module to load. When dealing with local files, it  specifically refers to the name of the file without the extension of the file.

```javascript
import Menu from './menu';
```

METHOD 2 (named)

```javascript
import { specialty, isVegetarian } from './menu';

console.log(specialty);

/*---------------------with alias-------------*/
import { chefsSpecial, isVeg, isLowSodium as saltFree } from './menu';

/*we must use the alias when it was set on export, unless it isn't set so it can be applied here at import*/

/*-------------import entire module as alias--------------*/
import * as Carte from './menu';

Carte.chefsSpecial;
Carte.isVeg();
Carte.isLowSodium();
```



1. Here `specialty` and `isVegetarian` are imported.
2. If we did not want to import either of these variables, we could omit them from the `import` statement.
3. We can then use these objects as in within our code. For example, we would use `specialty` instead of `Menu.specialty`. 

### Combining different exports

Note: Although what isn't exported won't be available directly/explicitly, it could be available indirectly as in the example below.

``` javascript
// moduleToExport.js
const uppercaseName = function (name) {
  return name.toUpperCase();
}

const myDefaultExport = {
  //...
}


class Animal {
  constructor(name){
    this._name = name;
  }
  get name () {
    return uppercaseName(this._name);
  }
}


export default myDefaultExport; //default export is the `myDefaultExport` object
export {Animal}; //named export `Animal` class, not exporting the `uppercaseName` function


//main.js
import myDefaultExport from './moduleToExport.js'; //importing default module `myDefaultExport`
import {Animal} from './moduleToExport.js'; //importing a named module, `Animal`

const animal = new Animal('test');
console.log(animal.name); //logs `TEST` to the console, uses the private `uppercaseName` function even though we don't have access to `uppercaseName` through our imported `Animal` module and cannot call it explicitly
```

## Error Handling

By catching errors you can prevent the program from stopping, and send a useful message to the user to understand what's happened.

Useful when using 3rd party code, for example you expect to receive an array but you might get a string!

```javascript
/*insert code that might cause an error in try...catch*/
try {
  throw Error('This error will get caught');//here goes error prone code
} catch (e) {
  console.log(e); // code that handles error goes here
}
// Prints: This error will get caught

console.log('The thrown error that was caught in the try...catch statement!');
// Prints: 'The thrown error that was caught in the try...catch statement!'
/*-------------------------------------------*/

const someVar = 'Cannot be reassigned';
try {
  someVar = 'Still going to try';
} catch(e) {
  console.log(e);
}
// Prints: TypeError: Assignment to constant variable.
```

You can make an error by using the error object **Error** , but this won't stop the program running. **throw**ing an error will. You can handle thrown errors with a **try..catch** statement. 

## Promises

Promises are JavaScript objects that represent the eventual result of an asynchronous operation.

```javascript
const promiseTheWorld = new Promise(
    (resolve,reject) => {
        ////asynchronous operations
        if(everythingok) resolve(resolvedValue);
        else if (errors) reject (error message);
    }
   )//end promise
    
PromisedTheWorld.then(successHandler,failureHandler)
//This is settled THEN this will execute
                                   

/*Javascript passes its OWN resolve and reject functions*/
const executorFunction = (resolve, reject) => {
  if (someCondition) {
      resolve('I resolved!');
  } else {
      reject('I rejected!'); 
  }
}

/*a promise takes an executor function which runs automatically when the
constructor is called. This starts an asynchronous operation and determines how it should be settled*/

const myFirstPromise = new Promise(executorFunction);
```

`resolve` is a function with one argument. Under the hood, if invoked, `resolve()` will change the promise’s status from `pending` to `fulfilled`, and the promise’s **resolved value will be set to the argument passed into `resolve()`**.

`reject` is a function that takes a reason or error as an argument. Under the hood, if invoked, `reject()` will change the promise’s status from `pending` to `rejected`, and the promise’s **rejection reason will be set to the argument passed into `reject()`**.

### fulfilled or rejected promises THEN

```javascript
/*this function randomly resolves or gets rejected*/
let prom = new Promise((resolve, reject) => {
  let num = Math.random();
  if (num < .5 ){
    resolve('Yay!'); //this is the resolved value
  } else {
    reject('Ohhh noooo!');
  }
});

const handleSuccess = (resolvedValue) => {//handler function
  console.log(resolvedValue);
};

const handleFailure = (rejectionReason) => {
  console.log(rejectionReason);
};

prom.then(handleSuccess, handleFailure);
/*THEN function is invoked FROM the promise, and we pass a success handler.*/



/*----------------A Real Example!------------------------*/

//app.js
const {checkInventory} = require('./library.js'); //import library

const order = [['sunglasses', 1], ['bags', 2]];

// handler functions
function handleSuccess(resolvedValue){
  console.log(resolvedValue);
}
function handleFailure(rejectionReason) {
  console.log(rejectionReason);
}
//attach handlers to promise returned by checkInventory
checkInventory(order).then(handleSuccess,handleFailure);
//Later see -> checkInventory(order).then(handleSuccess).catch(handleFailure);

/*------------------library.js---------------*/
//library.js
const inventory = {
    sunglasses: 1900,
    pants: 1088,
    bags: 1344
};

const checkInventory = (order) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => { //this is to make sure it is done asyncronously
            let inStock = order.every(item => inventory[item[0]] >= item[1]);
            if (inStock) {
                resolve(`Thank you. Your order was successful.`);
            } else {
                reject(`We're sorry. Your order could not be completed because some items are sold out.`);
            }
        }, 1000); //end setTimeout
    })//end promise
};

module.exports = { checkInventory };
```

`setTimeout()` is a Node function which delays the execution of a callback function using the event-loop. This is important to ensure asynchronicity.

`.then()` called without handler, will return a promise with the same settled value as the promise it was called on if no appropriate handler was provided. This means we can also do this

```javascript
/*use one THEN for the success, then another THEN for the failure*/
prom
  .then((resolvedValue) => {
    console.log(resolvedValue);
  })
  .then(null, (rejectionReason) => {
    console.log(rejectionReason);
  });

/*we can instead use another word CATCH which does the same as then, but with only a failure handler*/
prom
  .then((resolvedValue) => {
    console.log(resolvedValue);
  })
  .catch((rejectionReason) => { //this will be invoked if then fails
    console.log(rejectionReason);
  });
```

### Chaining and Composition

Promise composition enables us to write complex, asynchronous code that’s still readable. We do this by chaining multiple `.then()`‘s and `.catch()`‘s.

To use promise composition correctly, we have to remember to `return` promises constructed within a `.then()`.

```javascript
/*this allows the combination of multiple promises to that events can be done in the correct order*/

firstPromiseFunction()   //this returns a promise
.then((firstResolveVal) => { //successhandler
  return secondPromiseFunction(firstResolveVal);
    //return new 2nd promise with resolved value of 1st promise
})
.then((secondResolveVal) => {//handle second promise
  console.log(secondResolveVal);//success handler
});

/*----------------REAL Example------------------------*/
//app.js 

const {checkInventory, processPayment, shipOrder} = require('./library.js');

const order = {
  items: [['sunglasses', 1], ['bags', 2]],
  giftcardBalance: 79.82
};

/*Composition CHAINING, functions must return other promises!*/
checkInventory(order)
.then((resolvedValueArray) => {
  // Write the correct return statement here:
  return processPayment(resolvedValueArray);
})
.then((resolvedValueArray) => {
  // Write the correct return statement here:
  return shipOrder(resolvedValueArray);
})
.then((successMessage) => {
  console.log(successMessage);
})
.catch((errorMessage) => {
  console.log(errorMessage);
});

/*----------------------------library.js------------------------*/
const store = {
  sunglasses: {
    inventory: 817, 
    cost: 9.99
  },
  pants: {
    inventory: 236, 
    cost: 7.99
  },
  bags: {
    inventory: 17, 
    cost: 12.99
  }
};

const checkInventory = (order) => {
  return new Promise ((resolve, reject) => {
   setTimeout(()=> {  
   const itemsArr = order.items;  
   let inStock = itemsArr.every(item => store[item[0]].inventory >= item[1]);
   
   if (inStock){
     let total = 0;   
     itemsArr.forEach(item => {
       total += item[1] * store[item[0]].cost
     });
     console.log(`All of the items are in stock. The total cost of the order is ${total}.`);
     resolve([order, total]);
   } else {
     reject(`The order could not be completed because some items are sold out.`);
   }     
}, generateRandomDelay());
 });
};

const processPayment = (responseArray) => {
  const order = responseArray[0];
  const total = responseArray[1];
  return new Promise ((resolve, reject) => {
   setTimeout(()=> {  
   let hasEnoughMoney = order.giftcardBalance >= total;
   // For simplicity we've omited a lot of functionality
   // If we were making more realistic code, we would want to update the giftcardBalance and the inventory
   if (hasEnoughMoney) {
     console.log(`Payment processed with giftcard. Generating shipping label.`);
     let trackingNum = generateTrackingNumber();
     resolve([order, trackingNum]);
   } else {
     reject(`Cannot process order: giftcard balance was insufficient.`);
   }
   
}, generateRandomDelay());
 });
};


const shipOrder = (responseArray) => {
  const order = responseArray[0];
  const trackingNum = responseArray[1];
  return new Promise ((resolve, reject) => {
   setTimeout(()=> {  
     resolve(`The order has been shipped. The tracking number is: ${trackingNum}.`);
}, generateRandomDelay());
 });
};


// This function generates a random number to serve as a "tracking number" on the shipping label. In real life this wouldn't be a random number
function generateTrackingNumber() {
  return Math.floor(Math.random() * 1000000);
}

// This function generates a random number to serve as delay in a setTimeout() since real asynchrnous operations take variable amounts of time
function generateRandomDelay() {
  return Math.floor(Math.random() * 2000);
}

module.exports = {checkInventory, processPayment, shipOrder};
```

#### Avoiding Common Mistakes with Promises

* nesting promises instead of chaining them
* forgetting to return a promise (won't throw error, tricky to debug)

#### promise.all()

To take advantage of concurrency, we can use `Promise.all()`.

```javascript
let myPromises = Promise.all([returnsPromOne(), returnsPromTwo(), returnsPromThree()]);

myPromises
  .then((arrayOfValues) => {
    console.log(arrayOfValues);
  })
  .catch((rejectionReason) => {
    console.log(rejectionReason);
  });
```

- We declare `myPromises` assigned to invoking `Promise.all()`.
- We invoke `Promise.all()` with an array of three promises— the returned values from functions.
- We invoke `.then()` with a success handler which will print the array of resolved values if each promise resolves successfully. 
- We invoke `.catch()` with a failure handler which will print the first rejection message if any promise rejects. 

```javascript
//Example app.js
const {checkAvailability} = require('./library.js');

/*-------------Handlers---------------------------------*/
const onFulfill = (itemsArray) => {
  console.log(`Items checked: ${itemsArray}`);
  console.log(`Every item was available from the distributor. Placing order now.`);
};

const onReject = (rejectionReason) => {
	console.log(rejectionReason);
};

//----------------Collect promises------------------

let checkSunglasses = checkAvailability('sunglasses','Favorite Supply Co.');
let checkPants = checkAvailability('pants','Favorite Supply Co.');
let checkBags = checkAvailability('bags','Favorite Supply Co.');

//--------------composition/chaining of promises---------------------
const promiseArray = [checkSunglasses, checkPants, checkBags];
Promise.all(promiseArray).then(onFulfill).catch(onReject);






/*-----------library.js-------------------------*/

//this randomly decides if an item is available or not
const checkAvailability = (itemName, distributorName) => {
    console.log(`Checking availability of ${itemName} at ${distributorName}...`);
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (restockSuccess()) {
                console.log(`${itemName} are in stock at ${distributorName}`)
                resolve(itemName);
            } else {
                reject(`Error: ${itemName} is unavailable from ${distributorName} at this time.`);
            }
        }, 1000);
    });
};

module.exports = { checkAvailability };


// This is a function that returns true 80% of the time
// We're using it to simulate a request to the distributor being successful this often
function restockSuccess() {
    return (Math.random() > .2);
}

```

## Async Await (ES8)

Though async can use promise syntax then catch, there is no need to declare a new Promise object.

 ```javascript
/*Syntax */
async function myFunc() { // function declaration
  // Function body here
};
myFunc();

const myFunc = async () => { // function expression
  // Function body here
};
myFunc();
/*----------------------------------------------*/
async function fivePromise() { 
  return 5;
}

fivePromise()
.then(resolvedValue => {
    console.log(resolvedValue);
  })  // Prints 5

/*In the example above, even though we return 5 inside the function body, what’s actually returned when we invoke fivePromise() is a promise with a resolved value of 5. */
 ```

`async` functions always return a promise. This means we can use traditional promise syntax, like `.then()` and `.catch` with our `async` functions. An `async` function will return in one of three ways:

- If **nothing returned** from function, it will **return a promise with resolved value of `undefined`**.  nothing --> promise resolved to undefined
- If **non-promise value returned** from function, it will return **promise resolved to that value**. value --> promise resolved to value
- If a **promise is returned** from the function, it will simply **return that promise** promise --> promise

```javascript
//often promise functions are provided by an external library
async function asyncFuncExample(){
  let resolvedValue = await myPromise();//we wait for the value
  console.log(resolvedValue); //then we execute the code synchronously
}

asyncFuncExample(); // Prints: I am resolved now!
```

The `await` keyword can only be used inside an `async` function. `await` is an operator: it returns the resolved value of a promise. 

Since promises resolve in an indeterminate amount of time, `await` **halts**, or **pauses**, the execution of our `async` function until a given promise is resolved.

#### differences between promise and async

```javascript
//----------------DIFFERENCES BETWEEN METHODS-------------------------
/*----------------EXAMPLE -------------------------*/
const brainstormDinner = require('./library.js')
/*brainstormDinner() expects no arguments and returns a new promise with a resolved value of a string representing a meal. */

// Native promise version:
function nativePromiseDinner() {
  brainstormDinner().then((meal) => {
	  console.log(`I'm going to make ${meal} for dinner.`);
  })
}

//nativePromiseDinner();

// async/await version:
async function announceDinner() {
  let meal = await brainstormDinner();
  console.log(`I'm going to make ${meal} for dinner.`);
}
announceDinner();

/*------------------Example 1---------------------*/

const fs = require('fs');
const promisifiedReadfile = require('./promisifiedReadfile');
      
// -------Here we use fs.readfile() and callback functions:-------
fs.readFile('./file.txt', 'utf-8', (err, data) => {
  if (err) throw err;
  let firstSentence = data;
  fs.readFile('./file2.txt',  'utf-8', (err, data) => {
    if (err) throw err;
    let secondSentence = data;
    console.log(firstSentence, secondSentence)
  });
});

// Here we use native promises with our "promisified" version of readfile:
let firstSentence promisifiedReadfile('./file.txt', 'utf-8')
  .then((data) => {
    firstSentence = data;
    return promisifiedReadfile('./file2.txt', 'utf-8')
  })
  .then((data) => {
    let secondSentence = data;
    console.log(firstSentence, secondSentence)
  })
  .catch((err) => {console.log(err)});

// Here we use promisifiedReadfile() again but instead of using the native promise .then() syntax, we declare and invoke an async/await function:
async function readFiles() {
  let firstSentence = await promisifiedReadfile('./file.txt', 'utf-8')
  let secondSentence = await promisifiedReadfile('./file2.txt', 'utf-8')
  console.log(firstSentence, secondSentence)
}
readFiles()
/*----------------------------------EXAMPLE 2-------------------------------------------*/
    
function withConstructor(num){
  return new Promise(
    (resolve, reject) => { //executor function 
      if (num === 0) {resolve('zero');} //resolve
      else {resolve('not zero');} //resolve
      }
    )
}

withConstructor(0) //passes 0 to new promise
  .then((resolveValue) => { //resolves to string 'zero'
  console.log(` withConstructor(0) returned a promise which resolved to: ${resolveValue}.`);
})

// SAME CODE AS ASYNC

async function withAsync(num) {
  return num == 0 ? 'zero' : 'not zero'; // return promise with resolved value
}
/*This is possible because whatever is returned from async is a promise, so the promise declaration is not necessary*/

withAsync(100)
  .then((resolveValue) => {
  console.log(` withAsync(100) returned a promise which resolved to: ${resolveValue}.`);
})



```

#### Await

if you dont a**wait** you won't get what you ordered!

```javascript
/*The following code demostrates the importance of including the await keyword in an async block*/
let myPromise = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve('Yay, I resolved!')
    }, 1000);
  });
}

async function noAwait() {
 let value = myPromise();
 console.log(value);
}

async function yesAwait() {
 let value = await myPromise();
 console.log(value);
}

noAwait(); // Prints: Promise { <pending> }
yesAwait(); // Prints: Yay, I resolved!
```

### Dependent promises and async await

When one promise depends on another to run, you can use chaining or async await

```javascript
/*------promise chaining version-------*/
function nativePromiseVersion() {
    returnsFirstPromise()
    .then((firstValue) => {
        console.log(firstValue);
        //another promise function is called with new calculated value
        return returnsSecondPromise(firstValue); 
    })
   .then((secondValue) => {
        console.log(secondValue);
    });
}
/*----------Async Verion-----------*/
    
async function asyncAwaitVersion() {
 let firstValue = await returnsFirstPromise();
 console.log(firstValue);
 let secondValue = await returnsSecondPromise(firstValue);
 console.log(secondValue);
}
/*Async makes code more readable and easier to debug for this kind of operations*/

```

### Promises async await error handling

Note: When **catch** is used at the end of a chain of promises, it's difficult to understand where in the chain the caught error was created, making it difficult to debug. 

For *async* we can use a *try catch*!

```javascript
async function usingTryCatch() {
 try {
   let resolveValue = await asyncFunction('thing that will fail');
   let secondValue = await secondAsyncFunction(resolveValue);
 } catch (err) {
   // Catches any errors in the try block
   console.log(err);
 }
}

usingTryCatch();

//we could also use catch as a final catch in complex code
async function usingPromiseCatch() {
   let resolveValue = await asyncFunction('thing that will fail');
}

let rejectedPromise = usingPromiseCatch();
rejectedPromise.catch((rejectValue) => {
console.log(rejectValue);
})

```



### Concurrency in Async Await

```javascript
/*When functions don't depend on one another*/
async function concurrent() {
 const firstPromise = firstAsyncThing();
 const secondPromise = secondAsyncThing();
console.log(await firstPromise, await secondPromise);
}
```

Note: if we have multiple truly independent promises that we would like to execute fully in parallel, we must use individual `.then()` functions and avoid halting our execution with `await`. 

#### await promise all

```javascript
async function asyncPromAll() {
  const resultArray = await Promise.all([asyncTask1(), asyncTask2(), asyncTask3(), asyncTask4()]);
  for (let i = 0; i<resultArray.length; i++){
    console.log(resultArray[i]); 
  }
}
```

Promise all is good when we have multiple promises that don't depend on each other, but are ALL in any case required. Promise all has a **fail fast** which means if any of the promises fail, it will reject all with that reason. 



## HTTP TCP AJAX

HTTP is a language. TCP is the transport. 

Asynchronous JavaScript and XML (AJAX), enables requests to be made after the initial page load.

Writing GET and POST requests with XHR objects and vanilla JavaScript requires constructing the XHR object using `new`, setting the `responseType`, creating a function that will handle the response object, and opening and sending the request.

To add a query string to a URL endpoint you can use `?` and include a parameter.

To provide additional parameters, use `&` and then include a key-value pair, joined by `=`. 

Determining how to correctly write the requests and how to properly implement them  requires carefully reading the documentation of the API with which  you’re working.

### XHR GET Requests

Similarly, the XMLHttpRequest (XHR) API, named for XML, can be used to  make many kinds of requests and supports other forms of data. 

GET requests only request information from other sources. GET requests can be written using an XMLHttpRequest object and vanilla JavaScript.

```javascript
/// XMLHttpRequest GET

const xhr = new XMLHttpRequest(); // create a new XMLHttpReques object
const url = 'http://api-to-call.com/endpoint';

//Code that handles response
xhr.responseType = 'JSON'; //javascript object notation
xhr.onreadystatechange = () => {
    if (xhr.readyState === XMLHttpRequest.DONE){//if request finished
        //code to execute with response
        return xhr.response; 
        // this will contain data we're getting back from request
    }
};

xhr.open('GET',url); //opens request
xhr.send(); //send the xhr object to specified url

```

`.open()` creates a new request and the arguments passed in determine the type and URL of the request. 

#### XHR API call

```javascript
// Information to reach API
const url = 'https://api.datamuse.com/words?';
const queryParams = 'rel_jjb=';
const additionalParams = '&topics=';

// Selecting page elements
const inputField = document.querySelector('#input');
const topicField = document.querySelector('#topic');
const submit = document.querySelector('#submit');
const responseField = document.querySelector('#responseField');

// AJAX function
const getSuggestions = () => {
  //compose query to API
  const wordQuery = inputField.value;
  const topicQuery = topicField.value;
  const endpoint = `${url}${queryParams}${wordQuery}${additionalParams}${topicQuery}`;
  
  //compose / pack the object to send to the server / API
  const xhr = new XMLHttpRequest();
  xhr.responseType = 'json';
  xhr.onreadystatechange = () => {
    if (xhr.readyState === XMLHttpRequest.DONE) {
      renderResponse(xhr.response);
    }
  }
  
  xhr.open('GET', endpoint);
  xhr.send(); // send the object
}

// Clear previous results and display results to webpage
const displaySuggestions = (event) => {
  event.preventDefault();
  while(responseField.firstChild){
    responseField.removeChild(responseField.firstChild);
  }
  getSuggestions();
}

submit.addEventListener('click', displaySuggestions);


//-------------helperFunction.js

/ Formats response to look presentable on webpage
const renderResponse = (res) => {
  // handles if res is falsey
  if(!res){
    console.log(res.status)
  }
  // in case res comes back as a blank array
  if(!res.length){
    responseField.innerHTML = "<p>Try again!</p><p>There were no suggestions found!</p>"
    return
  }

  // creating an array to contain the HTML strings
  let wordList = []
  // looping through the response and maxxing out at 10
  for(let i = 0; i < Math.min(res.length, 10); i++){
    // creating a list of words
    wordList.push(`<li>${res[i].word}</li>`)
  }
  // joins the array of HTML strings into one string
  wordList = wordList.join("")

  // manipulates responseField to render the modified response
  responseField.innerHTML = `<p>You might be interested in:</p><ol>${wordList}</ol>`
  return
}

// Renders response before it is modified
const renderRawResponse = (res) => {
  // taking the first 10 words from res
  let trimmedResponse = res.slice(0, 10)
  //manipulates responseField to render the unformatted response
  responseField.innerHTML = `<text>${JSON.stringify(trimmedResponse)}</text>`
}

// Renders the JSON that was returned when the Promise from fetch resolves.
const renderJsonResponse = (res) => {
  // creating an empty object to store the JSON in key-value pairs
  let rawJson = {}
  for(let key in response){
    rawJson[key] = response[key]
  }
  // converting JSON into a string and adding line breaks to make it easier to read
  rawJson = JSON.stringify(rawJson).replace(/,/g, ", \n")
  // manipulates responseField to show the returned JSON.
  responseField.innerHTML = `<pre>${rawJson}</pre>`
}
```

### fetch() GET Requests - Alternative to XHR

The `fetch()` function:

- Creates a request object that contains relevant information that an API needs.
- Sends that request object to the API endpoint provided.
- Returns a promise that ultimately resolves to a response object, which contains the status of the promise with information the API sent back.

```javascript
//Fetch GET boilerplate

fetch('http://api-to-call.com/endpoint').then( // success handler
	response => {
        if (response.ok){//convert response to JSON object
            return response.json();
        }
         //handle errors - if response is falsy
        throw new Error('request failed!');
        //error handler - if we cannot reach endpoint at all-network error
    }, networkError => console.log(networkError.message)
).then(jsonResponse => { //with returned promise success handler
    // code to execute with jsonResponse
    return jsonResponse;
});


```

#### fetch() API request

```javascript
// Information to reach API
const url = 'https://api.datamuse.com/words';
const queryParams = '?sl=';

// Selects page elements
const inputField = document.querySelector('#input');
const submit = document.querySelector('#submit');
const responseField = document.querySelector('#responseField');

// AJAX function
const getSuggestions = () => {
//compose query to API  
  const wordQuery = inputField.value;
  const endpoint = `${url}${queryParams}${wordQuery}`;

//compose / pack the object to send to the server / API  
  fetch(endpoint, {cache: 'no-cache'}).then(response => {
    if (response.ok) {
      return response.json();
    }
    throw new Error('Request failed!');
  }, networkError => {
    console.log(networkError.message)
  }).then(jsonResponse =>{
    renderResponse(jsonResponse);
  })
}

/*OLD AJAX FUNCTION WITH XHR*/
const getSuggestions = () => {
  //compose query to API
  const wordQuery = inputField.value;
  const endpoint = `${url}${queryParams}${topicQuery}`;
  
  //compose / pack the object to send to the server / API
  const xhr = new XMLHttpRequest();
  xhr.responseType = 'json';
  xhr.onreadystatechange = () => {
    if (xhr.readyState === XMLHttpRequest.DONE) {
      renderResponse(xhr.response);
    }
  }
  
  xhr.open('GET', endpoint);
  xhr.send(); // send the object
}
/*END -----OLD AJAX FUNCTION WITH XHR*/




// Clears previous results and display results to webpage
const displaySuggestions = (event) => {
  event.preventDefault();
  while(responseField.firstChild){
    responseField.removeChild(responseField.firstChild);
  }
  getSuggestions();
};

submit.addEventListener('click', displaySuggestions);

```

### async fetch GET Request

```javascript
//async await GET boilerplate
//const getData = async () => {
async function getData() {
    try {
        //send request
        const response = await fetch('https://api-to-call.com/endpoint');
        //handle successful response
        if(response.ok) {
            //Code to execute with jsonResponse
            const jsonResponse = await response.json();
        }
        //handle unsuccessful response 
        throw new Error('Request failed!');
    } catch (error){
        console.log(error);
    }
}
```



#### async fetch API GET Request



```javascript
// Information to reach API
const url = 'https://api.datamuse.com/words?';
const queryParams = 'rel_jja=';

// Selecting page elements
const inputField = document.querySelector('#input');
const submit = document.querySelector('#submit');
const responseField = document.querySelector('#responseField');

// AJAX function
// Code goes here
const getSuggestions = async () => {
  const wordQuery = inputField.value;
  const endpoint = `${url}${queryParams}${wordQuery}`;
  try{
    const response = await fetch(endpoint,{cache: 'no-cache'});
    if(response.ok){
      const jsonResponse = await response.json();
      renderResponse(jsonResponse);
    }

  }catch(error){
    console.log(error);
  }
}


// Clear previous results and display results to webpage
const displaySuggestions = (event) => {
  event.preventDefault();
  while(responseField.firstChild){
    responseField.removeChild(responseField.firstChild)
  }
  getSuggestions();
}

submit.addEventListener('click', displaySuggestions);

```





### XHR POST Requests

POST methods can introduce new information to other sources in addition to requesting it.

````javascript

const xhr = new XMLHttpRequest(); // creates a new XHR object
const url = 'http://api-to-call.com/endpoint';
const data = JSON.stringify({id: '200'}); //converts data to string

//response handling
xhr.responseType = 'json';
xhr.onreadystatechange = () => {
    if(xhr.readyState === XMLHttpRequest.DONE){
        //code to execute with response
    }
};
//transmitting request
xhr.open('POST',url); //opens the request
xhr.send(data); // sends object
````





#### XHR API call POST

```javascript
// Information to reach API
const apiKey = '4fdeb0b541614931ac0d38bd0b490d28'; //API key
const url = 'https://api.rebrandly.com/v1/links';

// Some page elements
const inputField = document.querySelector('#input');
const shortenButton = document.querySelector('#shorten');
const responseField = document.querySelector('#responseField');

// AJAX functions
const shortenUrl = () => {
  //obtain and compose data in API readable format
  const urlToShorten = inputField.value;
  const data = JSON.stringify({destination: urlToShorten});
  
  //package data for sending in XHR format
  const xhr = new XMLHttpRequest();
  xhr.responseType = 'json';

  xhr.onreadystatechange = () => {
    if(xhr.readyState === XMLHttpRequest.DONE) {
      renderResponse(xhr.response); // action when object is ready
    }
  }

 // final setup
  xhr.open('POST',url);
  //necessary for rebrandly API
  xhr.setRequestHeader('Content-type','application/json');
  xhr.setRequestHeader('apikey',apiKey);
  xhr.send(data); // send everything
}


// Clear page and call AJAX functions
const displayShortUrl = (event) => {
  event.preventDefault();
  while(responseField.firstChild){
    responseField.removeChild(responseField.firstChild);
  }
  shortenUrl();
}

shortenButton.addEventListener('click', displayShortUrl);

//-------------------helperFunction.js

// Manipulates responseField to render a formatted and appropriate message
const renderResponse = (res) => {
  // Displays either message depending on results
  if(res.errors){
    responseField.innerHTML = "<p>Sorry, couldn't format your URL.</p><p>Try again.</p>";
  } else {  
    responseField.innerHTML = `<p>Your shortened url is: </p><p> ${res.shortUrl} </p>`;
  }
}

// Manipulates responseField to render an unformatted response
const renderRawResponse = (res) => {
  // Displays either message depending on results
  if(res.errors){  
    responseField.innerHTML = "<p>Sorry, couldn't format your URL.</p><p>Try again.</p>";
  } else {
    // Adds line breaks for JSON
    let structuredRes = JSON.stringify(res).replace(/,/g, ", \n");
    structuredRes = `<pre>${structuredRes}</pre>`;
    responseField.innerHTML = `${structuredRes}`;
  }
}

```

### fetch() POST Requests - Alternative to XHR

```javascript
//fetch POST boiler plate
fetch('http://api-to-call.com/endpoint', {
    method: 'POST', //this is a POST request
    body: JSON.stringify({id:'200'})}).then( //what type of info in POST
    response => {
        if(response.ok){
            return response.json();
        }
        throw new Error('Request failed!');//case status error
    },networkError => { //case error with network (down,unreachable)
        console.log(networkError.message);
    }).then(jsonResponse => {
    //code to execute with jsonResponse
    console.log(jsonResponse); // view json returned previously
});
```

#### fetch() POST Requests API

```javascript
// Information to reach API
const apiKey = '4fdeb0b541614931ac0d38bd0b490d28';
const url = 'https://api.rebrandly.com/v1/links';

// Some page elements
const inputField = document.querySelector('#input');
const shortenButton = document.querySelector('#shorten');
const responseField = document.querySelector('#responseField');

// AJAX functions
const shortenUrl = () => {
  const urlToShorten = inputField.value;
  const data = JSON.stringify({destination: urlToShorten});
  
  fetch(url, {method: 'POST',
  headers: {
    'Content-type': 'application/json',
    'apikey': apiKey
  }, 
  body: data // what is transfered to server
  }).then(
    response => {
      if(response.ok) {
        return response.json();
      }
      throw new Error('Request failed!');
  }, networkError => {
    console.log(networkError.message)
  }).then(jsonResponse => {
    renderResponse(jsonResponse);
  })

}

// Clear page and call AJAX functions
const displayShortUrl = (event) => {
  event.preventDefault();
  while(responseField.firstChild){
    responseField.removeChild(responseField.firstChild)
  }
  shortenUrl();
}

shortenButton.addEventListener('click', displayShortUrl);

/*-----------------helperFunction.js----------------*/

// Manipulates responseField to render a formatted and appropriate message
const renderResponse = (res) => {
  // Displays either message depending on results
  if(res.errors){
    responseField.innerHTML = "<p>Sorry, couldn't format your URL.</p><p>Try again.</p>";
  } else {  
    responseField.innerHTML = `<p>Your shortened url is: </p><p> ${res.shortUrl} </p>`;
  }
}

// Manipulates responseField to render an unformatted response
const renderRawResponse = (res) => {
  // Displays either message depending on results
  if(res.errors){  
    responseField.innerHTML = "<p>Sorry, couldn't format your URL.</p><p>Try again.</p>";
  } else {
    // Adds line breaks for JSON
    let structuredRes = JSON.stringify(res).replace(/,/g, ", \n");
    structuredRes = `<pre>${structuredRes}</pre>`;
    responseField.innerHTML = `${structuredRes}`;
  }
}

// Renders the JSON that was returned when the Promise from fetch resolves.
const renderJsonResponse = (response) => {
  // Creates an empty object to store the JSON in key-value pairs
  let rawJson = {}
  for(let key in response){
    rawJson[key] = response[key]
  }
  // Converts JSON into a string and adding line breaks to make it easier to read
  rawJson = JSON.stringify(rawJson).replace(/,/g, ", \n")
  // Manipulates responseField to show the returned JSON.
  responseField.innerHTML = `<pre>${rawJson}</pre>`
}

```



### async fetch POST Requests

```javascript
//async function getData()
const getData = async () => {
  try{
    const response = await fetch('https://api-to-call.com/endpoint',{
      method: 'POST',
      body: JSON.stringify({id: 200})
    });
    if(response.ok){
      const jsonResponse = await response.json();
      return jsonResponse;
    }
    throw new Error('Request failed!');

  } catch(error) {
    console.log(error);
  }
}
```

#### async fetch POST API Requests

```javascript
// information to reach API
const apiKey = '4fdeb0b541614931ac0d38bd0b490d28';
const url = 'https://api.rebrandly.com/v1/links';

// Some page elements
const inputField = document.querySelector('#input');
const shortenButton = document.querySelector('#shorten');
const responseField = document.querySelector('#responseField');

// AJAX functions
// Code goes here
const shortenUrl = async () => {
  //prepare data for api call
  const urlToShorten = inputField.value;
  const data = JSON.stringify({destination: urlToShorten});
  try{
    const response = await fetch(url,{
      method: 'POST',
      body: data,
      headers:{
        'Content-type': 'application/json',
        'apikey': apiKey
      }
    });
    if(response.ok){
     const jsonResponse = await response.json();
     renderResponse(jsonResponse);

    }

  } catch(error){
    console.log(error);
  }
}

// Clear page and call AJAX functions
const displayShortUrl = (event) => {
  event.preventDefault();
  while(responseField.firstChild){
    responseField.removeChild(responseField.firstChild);
  }
  shortenUrl();
}

shortenButton.addEventListener('click', displayShortUrl);
```

## Transpilation With Babel - COMPATABILITY

```bash
/*Create a JSON file with details about the project, for the moment fill in name and description*/

npm init

/*Install required packages. The D flag adds babel to the devDependencies in the JSON file created earlier*/
npm install babel-cli -D
npm install babel-preset-env -D

/*create a file to specify what javascript needs to be converted*/
touch .babelrc
/*opening the file enter the object:
{
  "presets": ["env"] 
}
env means ES6+*/

/*open project's JSON file and add the following:
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "build": "babel src -d lib"
}
*/

/*creates a new ES5 code file by running build with specified parameters
from the JSON file above*/
npm run build
```

The build script in the JSON file instructs:

- `babel` — The Babel command call responsible for transpiling code.
- `src` — Instructs Babel to transpile all JavaScript code inside the **src** directory.
- `-d` — Instructs Babel to write the transpiled code to a directory. 
- `lib` — Babel writes the transpiled code to a directory called `lib`. 

https://caniuse.com/ for general compatibility questions on JS ,CSS ,HTML features

Instructions

1. Initialize your project using `npm init` and create a directory called **src**

2. Install babel dependencies by running

   ```
   npm install babel-cli -D
   npm install babel-preset-env -D
   ```

3. Create a 

   .babelrc

    file inside your project and add the following code inside it:

   ```
   {
     "presets": ["env"]
   }
   ```

4. Add the following script to your 

   ```
   scripts
   ```

    object in 

   package.json

   :

   ```
   "build": "babel src -d lib"
   ```

5. Run `npm run build` whenever you want to transpile your code from your **src** to **lib** directories.



# React

## Get Started

- [ ] Install node js
- [ ] npx create-react-app
- [ ] npm start 
- [ ] Clean up all unnecessary code

## JSX - How is React different from HTML and Javascript

* In react you can just put the HTML inside javascript without having to inject it in any special way
* The ( ) after the return in a component allows us to indent the code
* `<></>` Are JSX fragments, which allow us to return multiple HTML elements as 1, which is what we're allowed to do
* JSX is a little different from HTML. For example with the keyword `class`, we need to use `className`, as `Class` is a reserved word in JS.
* Another difference, ALL tags have to be Self closed `<input />`or closed on purpose `<input></input>` even when HTML doesn't usually require it.
* Thanks to react, it's not necessary to do all the JavaScript calls such as getElementById().etc. You can have dynamic HTML off the bat!



``` java
//App.js
import React from 'react';

function App() {
  return (
    <>
      <div>
        <button>-</button>
        <span>0</span>
        <button>+</button>
      </div>
    </>
  )
}

export default App;
```



## Creating a Class Component

```react
import React, { Component } from 'react'

/*React allows us to write JSX, Component allows us to create a class
Being a class component, we're able to call render*/

export default class Counter extends Component {
  render() {
    return (
      <>
        <div>
          <button>-</button>
          <span>0</span>
          <button>+</button>
        </div>
      </>
    )
  }
}

/*Then on App.js, we're able to do this*/

import React from 'react';
import Counter from './Counter'

function App() {
  return (
    <Counter />
  )
}

export default App;
```



## Using props

``` react
import React from 'react';
import Counter from './Counter'

function App() {
  return (
    <Counter initialCount={0}/>
  )
}

/*Inside the JSX brackets we can pass in values, in this case initialCount.
By using curly braces, we can pass in javascript*/

export default App;

/*------------------Counter.js-------------------------*/

import React, { Component } from 'react'

/*We can then use the passed in variables using THIS.PROPS.variableWePassedIn
This gives us access to all variables passed in!*/

export default class Counter extends Component {
  render() {
    return (
      <>
        <div>
          <button>-</button>
          <span>{this.props.initialCount}</span>
          <button>+</button>
        </div>
      </>
    )
  }
}
```

## States - Make websites Reactive

### Class Components

```react
/*------------------Counter.js-------------------------*/
import React, { Component } from 'react'

//React allows us to write JSX, Component allows us to create a class

export default class Counter extends Component {
  constructor(props) {
    super(props)

    this.state = {
      count: props.initialCount
    }
  }

  render() {
    return (
      <>
        <div>
          <button onClick={()=> this.changeCount(-1)}>-</button>
          <span>{this.state.count}</span>
          <button onClick={()=> this.changeCount(+1)}>+</button>
        </div>
      </>
    )
  }

  changeCount(amount) {
    this.setState(prevState => { 
      return {count: this.state.count + amount }
    })
    //this.setState({ count: this.state.count + amount })
  }
}
  /*Every single class compoment has a THIS.SETSTATE, which takes an object
    and the object is going to be added in to the constructor's this.state
    by using Object.assign behind the scenes. This overwrites ONLY keys passed in
    
    However this.setState is an asynchronous function, so if we're
    changing the same thing twice in 1 call, it won't be done
    sequentially. 

    To make sure we have a sequential change, we use PREVSTATE function
    The function version makes sure we're using the previous state
    If we don't need the previous state, say we want to reset the counter
    then the non function version is fine. 
    
    */
```

### Functional Components - better alternative to Class Components

```react
import React, {useState} from 'react'

export default function CounterHooks(/*props*/{initialCount}) {

  const [count, setState] = useState(initialCount)
  //const [count, setState] = useState(initialCount)
  /*Potentially could have as many lines as arguments passed, breaking up the assignment and state updates*/

  return (
    <div>
          <button onClick ={ ()=> setState(prevCount => prevCount - 1)}>-</button>
          <span>{/*props.initialCount*/count}</span>
          <button onClick = {()=> setState(prevCount =>prevCount+ 1)}>+</button>
    </div>
  )
}



/* state as an object
return (
  <div>
        <button onClick ={
          ()=> setState(prevState => {
             return {count: state.count - 1}
            })}>-</button>
        <span>{state.count}</span>
        <button onClick = {()=> setState(prevState => {
             return {count: state.count + 1}
            })}>+</button>
  </div>
)*/

/*With functional compoments, we have all passed in variables in
props object, and we can use object deconstruction to get at them
individually if necessary

Since functional Components CAN'T have states, we call in useState
function as a hook, to allow us to have state functionality.

useState function takes in our initial state, in this case
{count: initialCount} returns our state as an array

Deconstructing the array, we have 2 values
Our state as assigned, in this case its {count: initialCount}
A function to change that state
These variables however, could have any other name

useState is really very similar to the constructor this.state =

Hooks really can use ANY kind of data as a state, so instead of using
an object, we can just use the direct value (in this case the number)

How is the information being saved?
Hooks rely on you CALLING the HOOKS always in the same order
This means
-Cannot call them in Conditionals
-Cannot call them in Loops
-Cannot put them in functions

You must call them at the TOP of the hook function (assign them)
*/
```

## Context

#### Context in Classes

```react
/*Usage in CLASS components*/

import React, { useState } from 'react';
import Counter from './Counter'
import CounterHooks from './CounterHooks'

export const ThemeContext = React.createContext();
//consumer = provider

function App() {
  const [theme, setTheme] = useState('red')
  return (
    <ThemeContext.Provider value={{ backgroundColor: theme }}>
    Counter
    <Counter initialCount={0}/>
    Counter Hooks
    <CounterHooks initialCount={0}/>
    <button onClick = {()=> setTheme(prevTheme => {
      return prevTheme === 'red' ? 'blue' : 'red'})}>Toggle Theme</button>
    </ThemeContext.Provider>
  )
}

export default App;

/*
Themes are a way of setting global variables, something that CAN'T
be done in react!

This way, all components within a theme, however deeply nested,
will have access to those variables.

Everything within ThemeContext will have access to values provided
*/

/*---------------------------Counter.js------------------*/
import React, { Component } from 'react'
import {ThemeContext} from './App'

//React allows us to write JSX, Component allows us to create a class

export default class Counter extends Component {
  constructor(props) {
    super(props)

    this.state = {
      count: props.initialCount
    }
  }

  render() {
    return (
      <ThemeContext.Consumer>
        {style => (

          <div>
            <button style = {style} onClick={() => this.changeCount(-1)}>-</button>
            <span>{this.state.count}</span>
            <button style = {style} onClick={() => this.changeCount(+1)}>+</button>
          </div>
        )}



      </ThemeContext.Consumer>

    )
  }

  changeCount(amount) {
    this.setState(prevState => {
      return { count: this.state.count + amount }
    })
    //this.setState({ count: this.state.count + amount })
  }
}
  /*
  ThemeContext needs to be imported with { } because it isn't a default export

  ThemeContext needs to have a function in it, within which our JSX will be rendered.

  The function has parenthesis instead of curly brackets, because the parenthesis tell
  the code to return back to the function

  Once setup, we have access to the style variable in all the code, it works like this
  1. Style(css) is set to {style} value, which is the default we put in useState
  2. When the button is pressed in App.js, it uses setTheme to change the style
  and this style is then propagated in all compoments that consume it.
  */
```

### Context in Function Components with Hooks

```react
//App.js stays the same as above!

import React, {useState, useContext} from 'react'
import {ThemeContext} from './App'

export default function CounterHooks(/*props*/{initialCount}) {

  const [count, setCount] = useState(initialCount)
  const style = useContext(ThemeContext)
  //const [count, setState] = useState(initialCount)
  /*Potentially could have as many lines as arguments passed, breaking up the assignment and state updates*/

  return (
    <div>
          <button style = {style} onClick ={ ()=> setCount(prevCount => prevCount - 1)}>-</button>
          <span>{/*props.initialCount*/count}</span>
          <button style = {style} onClick = {()=> setCount(prevCount =>prevCount+ 1)}>+</button>
    </div>
  )
}


/*
For hooks it's much easier
Import ThemeContext
create a hook const style =... this gives us access to the theme
Use variable to change styles (in this case)

EASY!!

One more note: Since the counters are the children of App.js, when
the toggle theme button is pressed, not only App.js is re-rendered
but also ALL it's children.
*/
```





# Advanced CSS

### Universal Reset (lowest specificy)

``` css
/*universal reset*/
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box; /*paddings and margins are no longer added to total size*/
}

body { /*set fonts in body, so all child*/
  font-family: "Lato", sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 1.7;
  color: #777;
  padding: 30px;
}
```

### Header

```css
.header {
  height: 95vh; /*fills 95% of the viewport*/
  
  /*settings for background with overlay*/
  background-image: linear-gradient(
    to right bottom,
    rgba(126, 213, 111, 0.80),
    rgba(40, 180, 133, 0.80)),
    url("../img/hero.jpg");
    
  background-size: cover;
  background-position: top; /*this makes sure top stays the same as image sizes and crops*/
  /*clip-path allows you to make shapes!
    https://bennettfeely.com/clippy/
    */  
  clip-path: polygon(0 0, 100% 0, 100% 75vh, 0 100%);
}
```

### Positioning

```css
/*For all of this to work, the parent element needs to be position: relative;
*/

/*When positioning you can always use*/
.logo-box {
  position: absolute;
  top: 40px;
  left: 40px;
}

/*Instead to get something to the centre, you can also use translate, as this can make sure that the elemement as in this case, doesn't BEGIN in the middle, but rather, its middle is in the middle!*/

.text-box {
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translate(-50%,-50%);
}
```

### Animation

```css
.heading-primary-sub {
  display: block;
  font-size: 20px;
  font-weight: 700;
  letter-spacing: 17.4px;
  
  animation: moveInRight 1s ease-out; /*This combines properties below*/
  /* animation: is short for all code below!
  animation-name: moveInRight;
  animation-duration: 1s;
  animation-timing-function: ease-out;
  */
}
/*This defines what animation does. Once defines it can be used for other effects such as hover: like a function!*/
@keyframes moveInRight { 
  0% {
    opacity: 0;
    transform: translateX(100px);
  }
  80% {
    transform: translateX(-10px);
  }
  100% {
    opacity: 1;
    transform: translate(0); /*removes all animation effects created*/
  }
}
```

### add further animations notes here

### Pseudo Elements

These result as virtual child elements, so they're added at the end. They can be used to add extra 'content' to the end with different styles, or as a clone, that you can style and animate, and could take the place of the original, as with the natours button. 

```css
.btn::after { /*treated as a child element of the button*/
  content: "";
  display: inline-block; /*we want it to look the same*/
  width: 100%; /*will be the size of the button*/
  height: 100%;
  border-radius: 100px;
  position: absolute; /*all this positioning to keep it behind the button*/
  top: 0;
  left: 0;
  z-index: -1; /*this is the order in which elements are overlayed*/
  transition: all .4s;
}

/*Absolute positioning works by finding first element with relative position,
and taking it from there.*/

/*Pseudo Elements :: are default last child element of tag. This is a virtual element.
In this case we make it exactly the same as the original, so as to create
an effect on the button, that is not the button itself!*/
.btn-white::after {
  background-color: #ffffff;
}

.btn:hover::after {
  transform: scaleX(1.4) scaleY(1.8);
  opacity: 0;
}

/*animation fill mode backwards automatically
applies styles of 0% before animation starts*/
.btn-animated{
  animation: moveInBottom .5s ease-out .75s;
  animation-fill-mode: backwards;
}
```

### How CSS values are processed (EM REM VH/VW %)

Understanding the structure of the document is SUPER important, because a lot of values are RELATIVE TO the PARENT ELEMENTS! 

#### A Percentage value (60%) 

* FONT-SIZE -> PARENT'S FONT SIZE
* LENGTH -> PARENT'S WIDTH

#### EM

Make Reference to;

* FONT-SIZE => PARENT'S FONT SIZE
* LENGTH => CURRENT ELEMENTS FONT SIZE

#### REM 

ALWAYS measured to document's ROOT!

#### VH VW

Percentage measurements of viewport's height and width



```css
/*
Fonts: Reference is parent elements
Lengths: Reference is current element
REM: ALWAYS uses ROOT font size
*/

html, body {
    font-size: 16px;
    width: 80vw; /*80% of viewport width*/
}

header {
    font-size: 150%;  /*(16px * 1.5) 24px*/
    padding: 2em; /*current element's padding(24px*2) 48px*/
    margin-bottom: 10rem; /*(16*10) 160px*/
    height: 90vh; /*(90% of current viewport height)*/
    width: 1000px; /*()*/
}

.header-child {
    font-size: 3em; /*(3*24) 72px*/
    padding: 10%; /*()*/
}

```



#### Inheritance

Every CSS element must have a value. (Generally from parent to child.)
Generally properties related to text are inherited, instead things to do with margins are not. Inherit property can force inheritance. 

Is there a cascaded value? - yes - take that

No - is the property inheritable? (some can be, some can't) yes - take that

No- The value becomes the initial value(for example padding becomes 0px)











## Three Pillars of writing GOOD HTML & CSS

### Responsive Design

* mobile first vs desktop first
* fluid layouts
* media queries
* responsive images
* correct units

### Maintainable and Scalable code

* clean
* easy to understand
* growth
* reusable
* how to organize files
* how to name classes
* how to structure HTML

### Web performance

* less HTTP requests
* less code
* compress code
* use a CSS pre-processor
* less images
* compress images





# Before Learning React

JavaScript concepts that helps to know when starting with React: 

- [x] ES6 classes
- [x]  Arrow functions
- [x] Let/const 
- [ ] Spread/Rest operators 
- [ ] Destructuring 
- [x] Map
- [x] Reduce
- [x] Filter 
- [x] Ternary operator 
- [x] Import and Export statements 
- [x] AJAX
- [x] Functions 
- [ ] High order functions

-----------------------------------------------------------------------------------------

## Further Resouces

https://github.com/gyazo/Gyazo-for-Linux