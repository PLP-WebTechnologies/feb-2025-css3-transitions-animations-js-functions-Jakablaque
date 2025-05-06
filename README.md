# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

Happy Coding! 💻✨

###*html*

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS Animation with JavaScript</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <button id="animButton">Click Me!</button>

  <script src="script.js"></script>
</body>
</html>


#### `style.css`

```css
/* Define the button style */
#animButton {
  padding: 20px 40px;
  font-size: 16px;
  cursor: pointer;
  border: none;
  background-color: #3498db;
  color: white;
  border-radius: 5px;
  transition: background-color 0.3s ease;  /* Smooth transition */
}

/* Animation for button when clicked */
@keyframes buttonAnimation {
  0% {
    transform: scale(1);
    background-color: #3498db;
  }
  50% {
    transform: scale(1.2);
    background-color: #e74c3c;  /* Change color */
  }
  100% {
    transform: scale(1);
    background-color: #3498db;
  }
}

.animate {
  animation: buttonAnimation 1s forwards;
}
```

#### `script.js`

```javascript
// Retrieve the button element
const animButton = document.getElementById('animButton');

// Function to store user preference in localStorage
function storeColorPreference(color) {
  localStorage.setItem('buttonColor', color);
}

// Function to apply the stored color preference
function applyStoredColor() {
  const storedColor = localStorage.getItem('buttonColor');
  if (storedColor) {
    animButton.style.backgroundColor = storedColor; // Apply stored color
  }
}

// Function to trigger the animation and change the color
function triggerAnimation() {
  // Add the animation class to the button
  animButton.classList.add('animate');
  
  // Store the new color in localStorage
  storeColorPreference('#e74c3c');  // Store red color for the button after click

  // Remove the animation class after animation is finished (to be able to replay)
  animButton.addEventListener('animationend', () => {
    animButton.classList.remove('animate');
  });
}

// Apply the stored color when the page loads
applyStoredColor();

// Add event listener to the button
animButton.addEventListener('click', triggerAnimation);
