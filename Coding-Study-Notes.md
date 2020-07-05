

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



## HTML FORMS

### Input tag  & Form Validation

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

When passing a function as an argument, pass the function directly, and where the function is defined, it can take the values of a usual for each function. 

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

### sort





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