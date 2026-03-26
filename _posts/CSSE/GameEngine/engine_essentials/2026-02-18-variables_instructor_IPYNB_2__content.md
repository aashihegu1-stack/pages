
## JavaScript Variables: From Games to Web Pages
Welcome! In this lesson, you’ll connect what you’ve already used in game code to the formal concepts of JavaScript variables, data types, and objects. The same patterns that control game state also power interactive web pages.

Learning Goal:

Understand how JavaScript variables and objects organize data in both games and web development.
- Practice using
  - let and const
  - object literals 
  - classes
  - object instantiation with new
  - dot notation
- SApply these same patterns to manipulating HTML elements through the DOM.

---

## Primitive Data Types

In game development, understanding the different data types in JavaScript is crucial for managing the various elements and attributes of a game or web site. Each type plays a unique role in creating a dynamic and interactive experience.

### Declaring Variables: `let` vs `const`

When you create (declare) a variable in JavaScript, you usually use either `let` or `const`:
- Use `let` when you want to create a variable that can change (mutable). For example, a player's score or health, which may go up or down during the game.
- Use `const` when you want to create a variable that should not be reassigned (immutable). For example, a player's name after login, or a unique ID for a game object. 

Each declared variable is given a type by JavaScript.

1. **Number**:
   - Represents numerical values, health and timeInMilliSeconds

2. **String**:
   - Represents text, such as the user's name or keypress.

3. **Boolean**:
   - Represents true/false values, such as isAlive.

4. **Undefined**:
   - Represents a variable that has been declared but not yet assigned a value.

5. **Null**:
   - Represents the intentional absence of any object value, such as an empty inventory slot.

6. **Symbol**:
   - Represents a unique and immutable value, often used as unique identifiers for game objects.

7. **BigInt**:
   - Represents very large integers, such as the total number of points accumulated over many games.




{% capture challenge0 %}
Observe Primitive Data Types and Reference Data Types in JavaScript
{% endcapture %}

{% capture code0 %}
/* Primitive Data Types
These are data types that store a single value.
*/

// Number: Represents numerical values, such as health and speed
let health = 100; // Integer (let: health may change during the game)
let playerSpeed = 5.75; // Float representing the player speed (let: speed may change)

console.log("Health (Number):", health, "Type:", typeof health);
console.log("Player Speed (Number):", playerSpeed, "Type:", typeof playerSpeed);

// String: Represents text, such as the user name or keypress
const userName = "Hero123"; // User name (const: name does not change after login)
let keyPress = 'a'; // Keypress (let: keyPress changes as user types)

console.log("User Name (String):", userName, "Type:", typeof userName);
console.log("Key Press (String):", keyPress, "Type:", typeof keyPress);

// Compare single character to its ASCII value
let asciiValue = keyPress.charCodeAt(0); // let: asciiValue changes with keyPress
console.log("ASCII Value of Key Press:", asciiValue, "Type:", typeof asciiValue);
console.log("Is Key Press 'a' (ASCII 97)?", asciiValue === 97);

// Boolean: Represents true/false values, such as isAlive
let isAlive = true; // let: isAlive may change during gameplay

console.log("Is Alive (Boolean):", isAlive, "Type:", typeof isAlive);

// Undefined: Represents a variable that has been declared but not yet assigned a value
let questReward; // let: questReward will be assigned later

console.log("Quest Reward (Undefined):", questReward, "Type:", typeof questReward);

// Null: Represents the intentional absence of any object value, such as an empty inventory slot
let inventorySlot = null; // let: inventorySlot may be filled later

console.log("Inventory Slot (Null):", inventorySlot, "Type:", typeof inventorySlot);

// Symbol: Represents a unique and immutable value, often used as unique identifiers for game objects
const uniqueID = Symbol('playerID'); // const: uniqueID never changes for this object

console.log("Unique ID (Symbol):", uniqueID, "Type:", typeof uniqueID);

// BigInt: Represents very large integers, such as the total time played in milliseconds
let totalTimePlayed = 1234567890123456789012345678901234567890n; // let: totalTimePlayed increases as you play

console.log("Total Time Played (BigInt):", totalTimePlayed, "Type:", typeof totalTimePlayed);
{% endcapture %}

{% capture source0 %}
```javascript
%%js

// CODE_RUNNER: Observe Primitive Data Types and Reference Data Types in JavaScript

/* Primitive Data Types
These are data types that store a single value.
*/

// Number: Represents numerical values, such as health and speed
let health = 100; // Integer (let: health may change during the game)
let playerSpeed = 5.75; // Float representing the player speed (let: speed may change)

console.log("Health (Number):", health, "Type:", typeof health);
console.log("Player Speed (Number):", playerSpeed, "Type:", typeof playerSpeed);

// String: Represents text, such as the user name or keypress
const userName = "Hero123"; // User name (const: name does not change after login)
let keyPress = 'a'; // Keypress (let: keyPress changes as user types)

console.log("User Name (String):", userName, "Type:", typeof userName);
console.log("Key Press (String):", keyPress, "Type:", typeof keyPress);

// Compare single character to its ASCII value
let asciiValue = keyPress.charCodeAt(0); // let: asciiValue changes with keyPress
console.log("ASCII Value of Key Press:", asciiValue, "Type:", typeof asciiValue);
console.log("Is Key Press 'a' (ASCII 97)?", asciiValue === 97);

// Boolean: Represents true/false values, such as isAlive
let isAlive = true; // let: isAlive may change during gameplay

console.log("Is Alive (Boolean):", isAlive, "Type:", typeof isAlive);

// Undefined: Represents a variable that has been declared but not yet assigned a value
let questReward; // let: questReward will be assigned later

console.log("Quest Reward (Undefined):", questReward, "Type:", typeof questReward);

// Null: Represents the intentional absence of any object value, such as an empty inventory slot
let inventorySlot = null; // let: inventorySlot may be filled later

console.log("Inventory Slot (Null):", inventorySlot, "Type:", typeof inventorySlot);

// Symbol: Represents a unique and immutable value, often used as unique identifiers for game objects
const uniqueID = Symbol('playerID'); // const: uniqueID never changes for this object

console.log("Unique ID (Symbol):", uniqueID, "Type:", typeof uniqueID);

// BigInt: Represents very large integers, such as the total time played in milliseconds
let totalTimePlayed = 1234567890123456789012345678901234567890n; // let: totalTimePlayed increases as you play

console.log("Total Time Played (BigInt):", totalTimePlayed, "Type:", typeof totalTimePlayed);

```
{% endcapture %}

{% include code-runner.html
   runner_id="game-essentials-variables-0"
   language="javascript"
   challenge=challenge0
   code=code0
   source=source0
%}


### Reference Data Types

When you define a reference type, it is typically declared with `const` so the reference (the link to the object or array) does not change. However, the values inside the object or array can still be updated as needed.

1. **Object**:
   - Represents a collection of key-value pairs, such as a player's attributes or game settings.

2. **Array**:
   - Represents an ordered collection of values, such as a list of high scores or inventory items.

3. **Function**:
   - Represents a block of code designed to perform a specific task, such as attacking an enemy or saving the game.




{% capture challenge1 %}
Observe Primitive Data Types and Reference Data Types in JavaScript
{% endcapture %}

{% capture code1 %}
/* Reference Data Types
These are data types that store references to memory locations.
*/

// Object: Represents a collection of key-value pairs, such as player attributes or game settings
const playerAttributes = {
  name: "Hero123", // const: playerAttributes object reference does not change
  health: 100,
  mana: 50
}; // (properties can change, but the object reference does not)

console.log("Player Attributes (Object):", playerAttributes, "Type:", typeof playerAttributes);

// Array: Represents an ordered collection of values, such as a list of high scores or inventory items
const highScores = [1500, 1200, 900, 600, 300]; // const: highScores array reference does not change

console.log("High Scores (Array):", highScores, "Type:", typeof highScores);

// Function: Represents a block of code designed to perform a specific task, such as attacking an enemy or saving the game
function attackEnemy() {
  console.log("Enemy attacked!");
} // function declarations are hoisted and do not need let/const

console.log("Attack Enemy (Function):", attackEnemy, "Type:", typeof attackEnemy);
attackEnemy();
{% endcapture %}

{% capture source1 %}
```javascript
%%js

// CODE_RUNNER: Observe Primitive Data Types and Reference Data Types in JavaScript

/* Reference Data Types
These are data types that store references to memory locations.
*/

// Object: Represents a collection of key-value pairs, such as player attributes or game settings
const playerAttributes = {
  name: "Hero123", // const: playerAttributes object reference does not change
  health: 100,
  mana: 50
}; // (properties can change, but the object reference does not)

console.log("Player Attributes (Object):", playerAttributes, "Type:", typeof playerAttributes);

// Array: Represents an ordered collection of values, such as a list of high scores or inventory items
const highScores = [1500, 1200, 900, 600, 300]; // const: highScores array reference does not change

console.log("High Scores (Array):", highScores, "Type:", typeof highScores);

// Function: Represents a block of code designed to perform a specific task, such as attacking an enemy or saving the game
function attackEnemy() {
  console.log("Enemy attacked!");
} // function declarations are hoisted and do not need let/const

console.log("Attack Enemy (Function):", attackEnemy, "Type:", typeof attackEnemy);
attackEnemy();
```
{% endcapture %}

{% include code-runner.html
   runner_id="game-essentials-variables-1"
   language="javascript"
   challenge=challenge1
   code=code1
   source=source1
%}


## JavaScript Objects

Objects in JavaScript are a way to group related variables (properties) and functions (methods) together. This lets you model real-world things or game elements in your code. For example, in a simple game, you might have a `GameObject` to represent a player, enemy, or item.

### Object Literals
You can create an object using curly braces `{}` and define its properties and methods inside:



{% capture challenge2 %}
Object literal with properties and methods
{% endcapture %}

{% capture code2 %}
const player = {
  name: 'Mario',
  score: 0,
  react: function() {
    console.log(this.name + ' is reacting!');
  }
};

console.log(player.name); // Access property with dot notation
player.react(); // Call method with dot notation
{% endcapture %}

{% capture source2 %}
```javascript
%%js

// CODE_RUNNER: Object literal with properties and methods

const player = {
  name: 'Mario',
  score: 0,
  react: function() {
    console.log(this.name + ' is reacting!');
  }
};

console.log(player.name); // Access property with dot notation
player.react(); // Call method with dot notation
```
{% endcapture %}

{% include code-runner.html
   runner_id="game-essentials-variables-2"
   language="javascript"
   challenge=challenge2
   code=code2
   source=source2
%}



### Classes and Instances
For more complex games, you can define a class and create multiple objects (instances) from it. This is how the `GameObject` works in your game code:



{% capture challenge3 %}
Class definition and instantiation
{% endcapture %}

{% capture code3 %}
class GameObject {
  constructor(name, x, y) {
    this.name = name;
    this.x = x;
    this.y = y;
  }
  move(dx, dy) {
    this.x += dx;
    this.y += dy;
  }
}

const player = new GameObject('Mario', 0, 0);
console.log(`Initial Player Position: (${player.x}, ${player.y})`); // 0 0
player.move(5, 3);
console.log(`Player Position after moving: (${player.x}, ${player.y})`); // 5 3
{% endcapture %}

{% capture source3 %}
```javascript
%%js

// CODE_RUNNER: Class definition and instantiation

class GameObject {
  constructor(name, x, y) {
    this.name = name;
    this.x = x;
    this.y = y;
  }
  move(dx, dy) {
    this.x += dx;
    this.y += dy;
  }
}

const player = new GameObject('Mario', 0, 0);
console.log(`Initial Player Position: (${player.x}, ${player.y})`); // 0 0
player.move(5, 3);
console.log(`Player Position after moving: (${player.x}, ${player.y})`); // 5 3

```
{% endcapture %}

{% include code-runner.html
   runner_id="game-essentials-variables-3"
   language="javascript"
   challenge=challenge3
   code=code3
   source=source3
%}


### Dot Notation
You use dot notation to access or change properties and methods of an object:
- `object.property` to get or set a value
- `object.method()` to call a function

This is the same pattern you'll use when working with HTML elements as objects in the DOM.



{% capture challenge4 %}
Class definition with properties, methods, and default values
{% endcapture %}

{% capture code4 %}
let gameSpeed = 10; // Global game speed variable

// Example of a class representing a game object
class GameObject {
  constructor(data) {
    // Using 'this' to define properties of the class instance
    this.image = data.image;
    this.width = data.width;
    this.height = data.height;
    this.speedRatio = data.speedRatio;
    // Position coordinates of the object are set to default values if arguments are not provided
    this.x = data.x;
    this.y = data.y;
    // Speed is calculated based on the global game speed and the speed ratio
    this.speed = gameSpeed * this.speedRatio;
    // Store the react callback if provided
    this.react = data.react || function() {
      console.log('No reaction defined');
    };
  }
}

const player_data = {
  image: 'player.png',
  width: 50,
  height: 50,
  speedRatio: 1.5,
  x: 0,
  y: 0,
  react: function() {
    console.log(`${this.image} is reacting at position (${this.x}, ${this.y})!`);
  }
};

const player = new GameObject(player_data);

console.log("Player Object (Class Instance):", player, "Type:", typeof player);
// Object reference
console.log("Player Image:", player.image);

// Activate the react callback
player.react();

const enemy_data = {
  image: 'enemy.png',
  width: 40,
  height: 40,
  speedRatio: 1.0,
  x: 100,
  y: 150
};

const enemy = new GameObject(enemy_data);
console.log("Enemy Object (Class Instance):", enemy, "Type:", typeof enemy);

// Object reference
console.log("Enemy Position:", `(${enemy.x}, ${enemy.y})`);
enemy.x += enemy.speed; // Move enemy based on its speed
console.log("Enemy New Position after moving:", `(${enemy.x}, ${enemy.y})`);
enemy.react(); // Enemy has default reaction
{% endcapture %}

{% capture source4 %}
```javascript
%%js

// CODE_RUNNER: Class definition with properties, methods, and default values

let gameSpeed = 10; // Global game speed variable

// Example of a class representing a game object
class GameObject {
  constructor(data) {
    // Using 'this' to define properties of the class instance
    this.image = data.image;
    this.width = data.width;
    this.height = data.height;
    this.speedRatio = data.speedRatio;
    // Position coordinates of the object are set to default values if arguments are not provided
    this.x = data.x;
    this.y = data.y;
    // Speed is calculated based on the global game speed and the speed ratio
    this.speed = gameSpeed * this.speedRatio;
    // Store the react callback if provided
    this.react = data.react || function() {
      console.log('No reaction defined');
    };
  }
}

const player_data = {
  image: 'player.png',
  width: 50,
  height: 50,
  speedRatio: 1.5,
  x: 0,
  y: 0,
  react: function() {
    console.log(`${this.image} is reacting at position (${this.x}, ${this.y})!`);
  }
};

const player = new GameObject(player_data);

console.log("Player Object (Class Instance):", player, "Type:", typeof player);
// Object reference
console.log("Player Image:", player.image);

// Activate the react callback
player.react();

const enemy_data = {
  image: 'enemy.png',
  width: 40,
  height: 40,
  speedRatio: 1.0,
  x: 100,
  y: 150
};

const enemy = new GameObject(enemy_data);
console.log("Enemy Object (Class Instance):", enemy, "Type:", typeof enemy);

// Object reference
console.log("Enemy Position:", `(${enemy.x}, ${enemy.y})`);
enemy.x += enemy.speed; // Move enemy based on its speed
console.log("Enemy New Position after moving:", `(${enemy.x}, ${enemy.y})`);
enemy.react(); // Enemy has default reaction
```
{% endcapture %}

{% include code-runner.html
   runner_id="game-essentials-variables-4"
   language="javascript"
   challenge=challenge4
   code=code4
   source=source4
%}


### Hack: GameObject Lives

**Why?**
Interactive programs depend on objects that store and update state. By extending your GameObject, you strengthen your understanding of classes, constructors, properties, and dot notation — core skills for both games and web apps.

**Task:**
Modify your GameObject to include a lives property.

Initialize it in the constructor.

Update it during gameplay (lose or gain lives).

Log changes to confirm it works.

Save work/file in your Porfolio repo.

**Task:**  
[Add-Lives Homework]({site.baseurl}/game/essentials/variables-hw)

## HTML Variables and the DOM

One of JavaScript’s primary roles is interacting with the Document Object Model (DOM) — the structured representation of a web page. Every HTML element on the page is an object. When you write JavaScript for a website, you are working with those objects.

### Finding and Using References

To modify an element, you first store a reference to it using methods like `getElementById()` or `querySelector()`.

Once you have that reference, you can read or change its properties — just like any other object.

### Dot Notation and Properties

After selecting an element, you use dot notation to modify its properties:

```js
const button = document.getElementById('my-btn'); // Get a reference to the button element
button.style.backgroundColor = 'blue'; // Change the background color
button.textContent = 'Clicked!'; // Change the button text
```

This follows the exact same pattern you use in game objects:

```js
const player = { name: 'Mario', score: 100 };
player.score += 10; // Update the score property
```

### Why This Matters
If you understand objects, you understand the DOM.
Web development is simply applying object manipulation to elements on a page.

The same variable patterns that move characters in a game also update text, style, and interaction in a browser.


<div class="ui-runner">


<!-- Button Container  -->
<div style="display: flex; flex-wrap: wrap; gap: 10px;">
    <a style="text-decoration: none;">
        <!-- Color Change Button with id -->
        <div id="color-btn-ui0" style="background-color: #00FF00; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold; cursor: pointer;">
            Color Change
        </div>
    </a>
    <a style="text-decoration: none;">
        <!-- Size Change Button with id -->
        <div id="size-btn-ui0" style="background-color: #FF0000; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold; cursor: pointer;">
            Size Change
        </div>
    </a>
    <a style="text-decoration: none;">
        <!-- Clicker Box with id -->
        <div id="clicker-box-ui0" style="background-color: #12ABFF; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold; cursor: pointer;">
            Clicks: <span id="click-count-ui0">0</span>
        </div>
    </a>
</div>

<script>
(function() {
// All JS code inside a function to allow multiple runs in Jupyter Notebook without conflicts 
(function() {

  // 1. Color Change
  // Define const variable for the color button by its ID
  const colorBtn = document.getElementById('color-btn-ui0'); 
  // Define isWhite variable to track current color state
  let isWhite = true;
  // Define an event listener for the button click event
  colorBtn.addEventListener('click', function() {
      // Toggle the button text color between white and black using setProperty with priority
      if (isWhite) {
          colorBtn.style.setProperty('color', 'black', 'important');
      } else {
          colorBtn.style.setProperty('color', 'white', 'important');
      }
      isWhite = !isWhite; // Toggle to opposite state
  });

  // 2. Size Change
  const sizeBtn = document.getElementById('size-btn-ui0');
  let isLarge = false;
  sizeBtn.addEventListener('click', function() {
      if (isLarge) {
          sizeBtn.style.padding = '10px 20px';
          sizeBtn.style.fontSize = '1em';
      } else {
          sizeBtn.style.padding = '20px 40px';
          sizeBtn.style.fontSize = '1.5em';
      }
      isLarge = !isLarge;
  });

  // 3. Clicker Box (Cookie Clicker)
  const clickerBox = document.getElementById('clicker-box-ui0');
  const clickCount = document.getElementById('click-count-ui0');
  let count = 0;
  clickerBox.addEventListener('click', function() {
      clickCount.textContent = ++count; 
  });

})(); // End Jupyter Notebook required function()
})();
</script>
</div>

```python
%%html

<!-- UI_RUNNER: Interactive DOM manipulation buttons -->

<!-- Button Container  -->
<div style="display: flex; flex-wrap: wrap; gap: 10px;">
    <a style="text-decoration: none;">
        <!-- Color Change Button with id -->
    </a>
    <a style="text-decoration: none;">
        <!-- Size Change Button with id -->
        <div id="size-btn" style="background-color: #FF0000; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold; cursor: pointer;">
            Size Change
        </div>
    </a>
    <a style="text-decoration: none;">
        <!-- Clicker Box with id -->
        <div id="clicker-box" style="background-color: #12ABFF; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold; cursor: pointer;">
            Clicks: <span id="click-count">0</span>
        </div>
    </a>
</div>

<script>
// All JS code inside a function to allow multiple runs in Jupyter Notebook without conflicts 
(function() {

  // 1. Color Change
  // Define const variable for the color button by its ID
  const colorBtn = document.getElementById('color-btn'); 
  // Define isWhite variable to track current color state
  let isWhite = true;
  // Define an event listener for the button click event
  colorBtn.addEventListener('click', function() {
      // Toggle the button text color between white and black using setProperty with priority
      if (isWhite) {
          colorBtn.style.setProperty('color', 'black', 'important');
      } else {
          colorBtn.style.setProperty('color', 'white', 'important');
      }
      isWhite = !isWhite; // Toggle to opposite state
  });

  // 2. Size Change
  const sizeBtn = document.getElementById('size-btn');
  let isLarge = false;
  sizeBtn.addEventListener('click', function() {
      if (isLarge) {
          sizeBtn.style.padding = '10px 20px';
          sizeBtn.style.fontSize = '1em';
      } else {
          sizeBtn.style.padding = '20px 40px';
          sizeBtn.style.fontSize = '1.5em';
      }
      isLarge = !isLarge;
  });

  // 3. Clicker Box (Cookie Clicker)
  const clickerBox = document.getElementById('clicker-box');
  const clickCount = document.getElementById('click-count');
  let count = 0;
  clickerBox.addEventListener('click', function() {
      clickCount.textContent = ++count; 
  });

})(); // End Jupyter Notebook required function()
</script>
```

## Hack: HTML/JavaScript buttons

Why?
Modern web pages are interactive because JavaScript modifies the DOM. This hack strengthens your ability to select elements, store references, and update properties using variables and dot notation.

Task:
Extend the existing buttons or create a new one.

Select the element using getElementById() or querySelector().

Modify at least one property (style, textContent, or similar).

Add an event listener that changes state when clicked.

Save work/file in your Porfolio repo.

**Task:**  
Peform [Add-Button Homework]({site.baseurl}/game/essentials/variables-hw)

