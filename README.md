Ethiopian Foods App — Technical Documentation
A fully client‑side nutrition tracking application focused on Ethiopian cuisine.
Built with HTML, CSS, and vanilla JavaScript, featuring a structured food database, dynamic UI rendering, local persistence, and modular logic.

⚙️ Architecture Overview
The application is a single‑page web app (SPA) implemented entirely in:

index.html (contains HTML, CSS, JS)

images/ (food images + placeholder)

There is no backend.
All state is stored in memory or localStorage.

🧱 Core Components
1. Foods Database (57 items)
A static JavaScript array:

js
const foods = [ ... ];
Each entry includes:

name

calories

protein

carbs

fat

category

image (4:3 aspect ratio)

This database is used to render the foods grid and populate meal entries.

2. Rendering Engine
The UI is rendered dynamically using DOM manipulation:

renderFoods()

renderMeals()

updateDailyOverview()

renderWeeklyView()

These functions are pure and re‑render only the required sections.

3. State Management
State is stored in a simple object:

js
const meals = {
  breakfast: [],
  lunch: [],
  dinner: [],
  snacks: []
};
Each meal entry contains:

js
{
  name: "Doro Wot x2",
  calories: 900,
  protein: 64,
  carbs: 36,
  fat: 52
}
State is updated through:

addToMeal()

removeFromMeal()

Daily totals are computed via getDailyTotals().

4. Weekly Persistence
Weekly data is stored in localStorage:

js
localStorage.setItem("ethiopian_week", JSON.stringify([...]));
The app:

Saves a day when the user clicks Save Day (JSON)

Keeps only the last 7 entries

Renders a weekly bar chart

5. Visualizations
Macro Bar
A horizontal bar showing macro density:

css
.macro-bar-fill {
  transition: width 0.2s ease-out;
}
Macro Pie Chart
Rendered using SVG paths:

js
drawMacroPie(protein, carbs, fat);
Weekly Bar Chart
Rendered using dynamic <div> elements with height scaling.

6. Recipe Modal System
Recipes are stored in:

js
const recipes = { ... };
The modal is controlled by:

openRecipeModal()

recipeClose event listener

7. Serving Size Scaling
Users can choose servings before adding a dish:

js
calories: food.calories * servings
8. Image Fallback Handling
If an image fails to load:

js
img.onerror = () => {
  img.src = "images/placeholder.jpg";
};
🎨 UI / UX
Design Principles
Dark theme

High contrast

Smooth animations

Responsive grid layout

4:3 image ratio for consistency

Minimalistic card‑based UI

Animations
Card fade‑in

Hover lift

Smooth bar transitions

📁 File Structure
Code
/
├── index.html        # Full application (HTML + CSS + JS)
├── images/
│   ├── doro_wot.jpg
│   ├── shiro_wot.jpg
│   ├── ...
│   └── placeholder.jpg
└── README.md
🚀 Deployment (GitHub Pages)
Push index.html and images/ to GitHub.

Go to Settings → Pages.

Set:

Source: main

Folder: / (root)

Save.

Your site becomes available at:

Code
https://<username>.github.io/<repo>/
🧪 Browser Compatibility
Tested on:

Chrome

Edge

Firefox

Safari

No frameworks → minimal compatibility issues.

🛠️ Tech Stack
Layer	Technology
UI	HTML5, CSS3
Logic	Vanilla JavaScript
Storage	localStorage
Charts	SVG + CSS
Deployment	GitHub Pages
🔒 Security Notes
No backend → no server‑side attack surface

No cookies

No external APIs

All data stays in the browser

📌 Future Enhancements
Light/dark mode toggle

Favorites system

Ingredient‑level nutrition

PDF export

Multi‑day planner

Search by macros
