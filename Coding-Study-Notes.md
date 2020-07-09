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

#### Destructuring ES6

##### Property Value Shorthand ES6 

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

##### destructured assignment

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

#### differences between promise and async

```javascript
//----------------DIFFERENCES BETWEEN METHODS------------------------------
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

- [ ] ES6 classes
- [x]  Arrow functions
- [ ] Let/const 
- [ ] Spread/Rest operators 
- [ ] Destructuring 
- [x] Map
- [ ] Reduce
- [x] Filter 
- [x] Ternary operator 
- [ ] Import and Export statements 
- [x] Functions 
- [ ] High order functions