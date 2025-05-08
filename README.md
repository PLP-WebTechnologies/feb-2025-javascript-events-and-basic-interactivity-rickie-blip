index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Event Management</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <h1>🎉 Welcome to EventPro 🎉</h1>

  <!-- Event Button -->
  <button id="clickBtn">Click Me!</button>

  <!-- Hover Box -->
  <div id="hoverBox">Hover over me!</div>

  <!-- Keypress Display -->
  <p id="keyDisplay">Press any key...</p>

  <!-- Secret Box -->
  <div id="secretBox">Double-click me for a surprise!</div>

  <!-- Interactive Button -->
  <button id="toggleBtn">Toggle Color</button>

  <!-- Image Gallery -->
  <div class="gallery">
    <img id="galleryImage" src="img1.jpg" alt="Event Photo" />
    <button id="nextBtn">Next</button>
  </div>

  <!-- Tabs -->
  <div class="tabs">
    <button class="tab" data-tab="details">Details</button>
    <button class="tab" data-tab="schedule">Schedule</button>
    <button class="tab" data-tab="contact">Contact</button>
  </div>
  <div id="tabContent">Select a tab to view content.</div>

  <!-- Registration Form -->
  <form id="regForm">
    <input type="text" id="name" placeholder="Full Name" required /><br/>
    <input type="email" id="email" placeholder="Email" required /><br/>
    <input type="password" id="password" placeholder="Password (min 8 chars)" required /><br/>
    <button type="submit">Register</button>
  </form>

  <!-- Footer Section -->
  <footer>
    <p>&copy; 2025 EventPro. All rights reserved.</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
style.css
body {
    font-family: Arial, sans-serif;
    padding: 20px;
    background: #f0f8ff;
  }
  
  h1 {
    color: #333;
    text-align: center;
  }
  
  #clickBtn, #toggleBtn, #nextBtn, .tab, form button {
    margin: 10px;
    padding: 10px 20px;
    cursor: pointer;
    background: #008cba;
    color: white;
    border: none;
    border-radius: 5px;
  }
  
  #hoverBox, #secretBox {
    padding: 20px;
    margin: 10px;
    background: #eee;
    border: 2px dashed #999;
    text-align: center;
  }
  
  .gallery img {
    width: 200px;
    height: auto;
    display: block;
    margin-bottom: 10px;
  }
  
  .tabs .tab {
    background: #ddd;
    margin-right: 5px;
  }
  
  #tabContent {
    margin-top: 20px;
    padding: 15px;
    background: #fff;
    border: 1px solid #21837e;
  }
  
  input {
    margin: 5px;
    padding: 10px;
    width: 250px;
  }
  
  input:invalid {
    border-color: red;
  }
  
  input:valid {
    border-color: green;
  }
  script.js
  // Button Click
const clickBtn = document.getElementById("clickBtn");
clickBtn.addEventListener("click", () => alert("You clicked the button!"));

// Hover Effect
const hoverBox = document.getElementById("hoverBox");
hoverBox.addEventListener("mouseenter", () => hoverBox.style.backgroundColor = "lightblue");
hoverBox.addEventListener("mouseleave", () => hoverBox.style.backgroundColor = "#eee");

// Keypress Detection
const keyDisplay = document.getElementById("keyDisplay");
document.addEventListener("keydown", e => {
  keyDisplay.textContent = `You pressed: ${e.key}`;
});

// Secret Double Click
const secretBox = document.getElementById("secretBox");
secretBox.addEventListener("dblclick", () => alert("🎉 Secret unlocked! 🎉"));

// Toggle Button Color
const toggleBtn = document.getElementById("toggleBtn");
let toggled = false;
toggleBtn.addEventListener("click", () => {
  toggled = !toggled;
  toggleBtn.style.backgroundColor = toggled ? "#4CAF50" : "#008cba";
  toggleBtn.textContent = toggled ? "Toggled!" : "Toggle Color";
});

// Image Gallery
const images = ["img1.jpg", "img2.jpg", "img3.jpg"];
let imgIndex = 0;
const galleryImage = document.getElementById("galleryImage");
const nextBtn = document.getElementById("nextBtn");
nextBtn.addEventListener("click", () => {
  imgIndex = (imgIndex + 1) % images.length;
  galleryImage.src = images[imgIndex];
});

// Tabs
const tabButtons = document.querySelectorAll(".tab");
const tabContent = document.getElementById("tabContent");
const tabData = {
  details: "Welcome to our Event! Join us for a day of fun and learning.",
  schedule: "9 AM - Registration, 10 AM - Workshops, 1 PM - Lunch, 3 PM - Closing.",
  contact: "Email us at contact@eventpro.com or call 123-456-7890."
};
tabButtons.forEach(btn => {
  btn.addEventListener("click", () => {
    const tab = btn.dataset.tab;
    tabContent.textContent = tabData[tab];
  });
});

// Form Validation
const regForm = document.getElementById("regForm");
const email = document.getElementById("email");
const password = document.getElementById("password");

email.addEventListener("input", () => {
  const valid = /^[^\\s@]+@[^\\s@]+\\.[^\\s@]+$/.test(email.value);
  email.style.borderColor = valid ? "green" : "red";
});

password.addEventListener("input", () => {
  password.style.borderColor = password.value.length >= 8 ? "green" : "red";
});

regForm.addEventListener("submit", e => {
  if (!email.value || !password.value || password.value.length < 8) {
    alert("Please complete the form correctly.");
    e.preventDefault();
  } else {
    alert("Successfully Registered!");
  }
});
