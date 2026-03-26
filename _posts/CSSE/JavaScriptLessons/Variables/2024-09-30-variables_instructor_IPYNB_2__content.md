
## JavaScript Variables: From Games to Web Pages

Welcome! In this lesson, you'll connect what you've already explored in game code to the formal concepts of JavaScript variables, data types, and objects. We'll explore how these ideas power both games and interactive web pages. 

**Lesson Goal:**
- Understand how JavaScript variables and objects work, and why they matter in both games and web development.
- Practice using `let` and `const`, object literals, classes, and dot notation.
- See how the same patterns apply to manipulating HTML elements (the DOM) with JavaScript.

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

### Reference Data Types

When you define a reference type, it is typically declared with `const` so the reference (the link to the object or array) does not change. However, the values inside the object or array can still be updated as needed.

1. **Object**:
   - Represents a collection of key-value pairs, such as a player's attributes or game settings.

2. **Array**:
   - Represents an ordered collection of values, such as a list of high scores or inventory items.

3. **Function**:
   - Represents a block of code designed to perform a specific task, such as attacking an enemy or saving the game.


```javascript
%%js

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

### Popcorn Hack: snake.md variables

**Why?**  
Recognizing how variables are used in code is critical for understanding game state and making effective modifications. By abstracting a few examples, you show you can read and reason about real code.

**Task:**  
Peform Let-Const Homework

## JavaScript Objects

Objects in JavaScript are a way to group related variables (properties) and functions (methods) together. This lets you model real-world things or game elements in your code. For example, in a simple game, you might have a `GameObject` to represent a player, enemy, or item.

### Object Literals
You can create an object using curly braces `{}` and define its properties and methods inside:

```js
const player = {
  name: 'Mario',
  score: 0,
  jump: function() {
    console.log(this.name + ' jumps!');
  }
};

console.log(player.name); // Access property with dot notation
player.jump(); // Call method with dot notation
```

### Classes and Instances
For more complex games, you can define a class and create multiple objects (instances) from it. This is how the `GameObject` works in your game code:

```js
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
player.move(5, 3);
console.log(player.x, player.y); // 5 3
```

### Dot Notation
You use dot notation to access or change properties and methods of an object:
- `object.property` to get or set a value
- `object.method()` to call a function

This is the same pattern you'll use when working with HTML elements as objects in the DOM.




```javascript
%%js

let gameSpeed = 10; // Global game speed variable

// Example of a class representing a game object
class GameObject {
  constructor(image, width, height, speedRatio = 0, x = 0, y = 0) {
    // Using 'this' to define properties of the class instance
    this.image = image;
    this.width = width;
    this.height = height;
    this.speedRatio = speedRatio;
    // Position coordinates of the object are set to default values if arguments are not provided
    this.x = x;
    this.y = y;
    // Speed is calculated based on the global game speed and the speed ratio
    this.speed = gameSpeed * this.speedRatio;
  }
}

const player  = new GameObject('player.png', 50, 50, 1.5 );
console.log("Player Object (Class Instance):", player, "Type:", typeof player);
// Object reference
console.log("Player Image:", player.image);

const enemy = new GameObject('enemy.png', 40, 40, 1.0, 100, 150);
console.log("Enemy Object (Class Instance):", enemy, "Type:", typeof enemy);
// Object reference
console.log("Enemy Position:", `(${enemy.x}, ${enemy.y})`);
enemy.x += enemy.speed; // Move enemy based on its speed
console.log("Enemy New Position after moving:", `(${enemy.x}, ${enemy.y})`);
```

### Popcorn Hack: GameObject lives

**Why?**
Adding and modifying properties in objects is a core skill for building interactive programs. By customizing your `GameObject`, you practice using classes, constructors, and dot notation—skills you'll use in both games and web apps.

**Task:**  
Peform Add-Lives Homework

## HTML variables and the DOM as an Object Store

When working with JavaScript, one of its primary purposes is to interact with the Document Object Model (DOM) of a web page. The DOM is a structured representation of the HTML elements on the page, and you can think of it as a giant object store. Each element in the DOM is an object, and you can access and manipulate these objects using JavaScript.

### Finding and Using References
To interact with an element, you first find a reference to it—often using methods like `getElementById` or `querySelector`. This is similar to how you work with object literals in JavaScript: you get a reference to an object, and then you can read or change its properties.

### Dot Notation and Attributes
Once you have a reference to a DOM element, you use dot notation to access or modify its attributes and properties. For example, you can change the `style`, `textContent`, or other properties directly:

```js
const button = document.getElementById('my-btn'); // Get a reference to the button element
button.style.backgroundColor = 'blue'; // Change the background color
button.textContent = 'Clicked!'; // Change the button text
```

This is very similar to how you interact with any JavaScript object:

```js
const player = { name: 'Mario', score: 100 };
player.score += 10; // Update the score property
```

### Why This Matters
Understanding that HTML elements are objects lets you use all your knowledge of variables, data types, and object manipulation in JavaScript to create interactive and dynamic web pages. The DOM is your playground, and JavaScript is the tool you use to shape it.


```python
%%html

<!-- Button Container  -->
<div style="display: flex; flex-wrap: wrap; gap: 10px;">
    <a style="text-decoration: none;">
        <!-- Color Change Button with id -->
        <div id="color-btn" style="background-color: #00FF00; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold; cursor: pointer;">
            Color Change
        </div>
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
      // Tooggle the button text color between white and black
      colorBtn.style.color = isWhite ? 'black' : 'white'; 
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



<!-- Button Container  -->
<div style="display: flex; flex-wrap: wrap; gap: 10px;">
    <a style="text-decoration: none;">
        <!-- Color Change Button with id -->
        <div id="color-btn" style="background-color: #00FF00; color: white; padding: 10px 20px; border-radius: 5px; font-weight: bold; cursor: pointer;">
            Color Change
        </div>
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
      // Tooggle the button text color between white and black
      colorBtn.style.color = isWhite ? 'black' : 'white'; 
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



## Hack: HTML/JavaScript buttons

**Why?**  
Working with the DOM using JavaScript is the primary skill of web page development. This hack helps you practice reading, modifying, and extending real JavaScript/HTML code—just like you'll do in real projects!

**Task:**  
Peform Add-Button Homework

