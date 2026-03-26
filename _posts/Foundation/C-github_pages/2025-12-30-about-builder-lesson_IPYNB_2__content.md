
## Interactive Flag Grid Builder

This lesson teaches you to build a grid of flags for the about.md using JavaScript DOM manipulation. You'll learn to:

1. **Create HTML containers** with JavaScript
2. **Style with CSS Grid** for responsive layouts
3. **Build data arrays** with JavaScript objects
4. **Loop through data** to generate dynamic content

Each exercise provides **live visual feedback** and lets you **copy the final code** to paste into your about.md page.

### Complete About personalization

Follow the Software Development Life Cycle (SDLC), by making code edits, run `make`, test, and commit.

1. **Section 1 -- Past Grid Buildier code:** make, test, commit
2. **Section 2 -- Edit and personalize markdown** make, test, commit
3. **Section 3 -- Change images to personalized photos** make, test, commit

Each section will create a new commit in your GitHub analytics, a minimimu of 3 commits should be created with this excercise.
---

## Step 1: Create the HTML Container using JavaScript
{% capture challenge1 %}
Create a div element with id "grid_container", style it, and add some sampletext inside.
{% endcapture %}

{% capture code1 %}
// Clear the output
outputElement.innerHTML = '';

// Create a div container with id
const container = document.createElement('div');
container.id = 'grid_container';

// Style the container 
container.style.border = '2px dashed';
container.style.padding = '10px';

// Add sample text
container.textContent = 'Container for grid created!.';

// Add containter to output 
outputElement.appendChild(container);
{% endcapture %}

{% include ui-runner.html
   runner_id="step1"
   challenge=challenge1
   code=code1
   height="250px"
   output_height="100px"
%}
---

## Step 2: Demostrate CSS styling for a grid layout
{% capture challenge2 %}
Set container style elements for the grid_container to display generated items in a grid layout. 
{% endcapture %}

{% capture code2 %}
// Clear the output
outputElement.innerHTML = '';

// Create a div container with id
const container = document.createElement('div');
container.id = 'grid_container';

// Style the container 
container.style.border = '2px dashed';
container.style.padding = '10px';

// Grid specific styles
container.style.display = 'grid';
container.style.gridTemplateColumns = 'repeat(auto-fill, minmax(150px, 1fr))';

// Add sample grid items
for (let i = 1; i <= 4; i++) {
  const item = document.createElement('div');
  item.style.padding = '20px';
  item.style.textAlign = 'center';
  item.style.borderRadius = '8px';
  item.style.border = '1px solid';
  item.textContent = 'Grid Item ' + i;
  container.appendChild(item);
}

// Add containter to output 
outputElement.appendChild(container);
{% endcapture %}

{% include ui-runner.html
   runner_id="step2"
   challenge=challenge2
   code=code2
   output_height="100px"
%}
---

## Step 3: Focus on the Flag Data Array
{% capture challenge3 %}
Create the data array with flag information. Add your own location to personalize it!
{% endcapture %}

{% capture code3 %}
// Clear the output
outputElement.innerHTML = '';

// Define the data array of flagobjects
const living_in_the_world = [
  {
    flag: "https://upload.wikimedia.org/wikipedia/commons/0/01/Flag_of_California.svg",
    greeting: "Hey",
    description: "California - forever"
  },
  {
    flag: "https://upload.wikimedia.org/wikipedia/commons/b/b9/Flag_of_Oregon.svg",
    greeting: "Hi",
    description: "Oregon - 9 years"
  },
  {
    flag: "https://upload.wikimedia.org/wikipedia/commons/b/be/Flag_of_England.svg",
    greeting: "Alright mate",
    description: "England - 2 years"
  },
  {
    flag: "https://upload.wikimedia.org/wikipedia/commons/e/ef/Flag_of_Hawaii.svg",
    greeting: "Aloha",
    description: "Hawaii - 2 years"
  }
];

// Create a pre container with id
const container = document.createElement('pre');
container.id = 'grid_container';

/// Style the container for JSON display 
container.style.border = '2px dashed';
container.style.padding = '10px';
container.style.borderRadius = '8px';
container.style.overflow = 'auto';

// Add the Flag data as JSON text 
container.textContent = JSON.stringify(living_in_the_world, null, 2);

// Add containter to output 
outputElement.appendChild(container);
{% endcapture %}

{% include ui-runner.html
   runner_id="step3"
   challenge=challenge3
   code=code3
%}
---

## Step 4: Complete Flag Grid for About Page 
{% capture challenge4 %}
Build the complete flag grid by looping through the data and creating styled grid items. 
{% endcapture %}

{% capture code4 %}
// Clear the output
outputElement.innerHTML = '';

// Data array
const living_in_the_world = [
  {flag: "https://upload.wikimedia.org/wikipedia/commons/0/01/Flag_of_California.svg", greeting: "Hey", description: "California - forever"},
  {flag: "https://upload.wikimedia.org/wikipedia/commons/b/b9/Flag_of_Oregon.svg", greeting: "Hi", description: "Oregon - 9 years"},
  {flag: "https://upload.wikimedia.org/wikipedia/commons/b/be/Flag_of_England.svg", greeting: "Alright mate", description: "England - 2 years"},
  {flag: "https://upload.wikimedia.org/wikipedia/commons/e/ef/Flag_of_Hawaii.svg", greeting: "Aloha", description: "Hawaii - 2 years"}
];

// Create a div container with id
const container = document.createElement('div');
container.id = 'grid_container';

// Style the container 
container.style.border = '2px solid';
container.style.padding = '10px';

// Grid specific styles
container.style.display = 'grid';
container.style.gridTemplateColumns = 'repeat(auto-fill, minmax(150px, 1fr))';
container.style.gap = '10px';

// Loop through data and create grid items
for (const location of living_in_the_world) {
  // Create grid item
  const gridItem = document.createElement('div');
  gridItem.style.textAlign = 'center';
  
  // Create a flag image
  const img = document.createElement('img');
  img.src = location.flag;
  img.alt = location.description + ' Flag';
  img.style.width = '100%';
  img.style.height = '100px';
  img.style.objectFit = 'contain';
  
  // Create a description
  const description = document.createElement('p');
  description.textContent = location.description;
  description.style.margin = '5px 0';
  description.style.fontWeight = 'bold';
  
  // Create a greeting
  const greeting = document.createElement('p');
  greeting.textContent = location.greeting;
  greeting.style.margin = '5px 0';
  greeting.style.fontStyle = 'italic';
  greeting.style.opacity = '0.7';
  
  // Add all elements to grid item
  gridItem.appendChild(img);
  gridItem.appendChild(description);
  gridItem.appendChild(greeting);
  
  // Add grid item to container
  container.appendChild(gridItem);
}

// Add containter to output 
outputElement.appendChild(container);
{% endcapture %}

{% include ui-runner.html
   runner_id="step4"
   challenge=challenge4
   code=code4
   height="400px"
%}
---

## How to Use Step 4 Code in Your about.md

When you copy code from the UI Builder to your about.md, you need to add setup lines to make `outputElement` work. The Setup linces creaate a grid container, assigns output element to the container.  Alsoo, they enclose javascript code inside of script tags.

```markdown
// Setup: lines from here to "Copy"
<div id="grid_container"></div>

<script>
var outputElement = document.getElementById("grid_container");

// ⬇️ Copy Start: start on outputElement.innerHTML line 
outputElement.innerHTML = '';
... All ui runner code from Step 4 here
outputElement.appendChild(container);
// ⬆️ Copy End: end on outputElement.appendChild line


// Setup: be sure to include end script tag
</script>
```

---

## For Other Content: Use Markdown & HTML

The UI Builder is great for JavaScript-heavy components like the flag grid. But for other content like image galleries, we will use Markdown and HTML directly.  Mix and match code types; Use JavaScript for dynamic grids, Markdown for descriptions, and HTML for gallery! We are doing all three to get familiar with the different options.

### Example: Image Gallery with HTML

```markdown
## Photo Gallery

<div class="image-gallery">
  <img src="{{site.baseurl}}/images/about/photo1.jpg" alt="Photo 1">
  <img src="{{site.baseurl}}/images/about/photo2.jpg" alt="Photo 2">
  <img src="{{site.baseurl}}/images/about/photo3.jpg" alt="Photo 3">
</div>

<style>
.image-gallery {
  display: flex;
  flex-wrap: nowrap;
  overflow-x: auto;
  gap: 10px;
}

.image-gallery img {
  max-height: 150px;
  object-fit: cover;
  border-radius: 5px;
}
</style>
```

### Example: Text with Markdown

```markdown
## Journey through Life

- 🏫 High School in Glendale (CA)
- 🎓 University of Oregon (Go Ducks!)
- 👨‍🏫 Teacher at Del Norte High School
```


---

## Hacks for about.md

1. **Customize the flag data:**
   - Learn about parts of JavaScript program.
   - Change the flag URLs with places you've lived or been. Make it personal.
2. **Copy the code** from the final challenge using the Copy Code button
2. **Customize the about.md code:**
   - Paste the flag code in Section 1, be mindful of important parts of code to maintain, review is above.
3. **Update Sections 2 and 3**
   - Update greetings and descriptions in Markdown to match your interests or history.
   - Change image paths to your own photo gallery, place files in image directory and use site.basurl.
3. **Test locally** with `make` to see your changes

