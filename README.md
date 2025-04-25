<!--
Project: University Educational Website
Technologies: HTML, CSS, JavaScript
Structure:
  /index.html            — Home
  /about.html            — About Us
  /courses.html          — Courses Overview (static list)
  /course-detail.html    — Individual Course (dynamic)
  /blog.html             — News & Articles
  /contact.html          — Contact Form
  /resources.html        — Learning Resources
  /events.html           — Campus Events
  /faq.html              — Frequently Asked Questions
  /testimonials.html     — Student Testimonials
  /signup.html           — Student Registration (with password checker)
  /css/style.css         — Global Stylesheet
  /js/main.js            — Shared Scripts (nav, smooth scroll)
  /js/courses.js         — Fetch & render course data
  /js/form.js            — Contact form handling logic
  /js/password.js        — Password strength checker
  /data/courses.json     — Course metadata (for dynamic page)
  /assets/               — Images, icons, fonts, etc.
  README.md              — GitHub Deployment & Usage
-->

<!-- signup.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sign Up</title>
  <link rel="stylesheet" href="css/style.css">
</head>
<body>
  <header>…</header>
  <main>
    <h1>Create an Account</h1>
    <form id="signup-form">
      <label>Email: <input type="email" required></label>
      <label>Password:
        <input type="password" id="password" required>
        <meter max="4" id="strength-meter"></meter>
        <p id="strength-text"></p>
      </label>
      <button type="submit">Register</button>
    </form>
  </main>
  <footer>…</footer>
  <script src="js/main.js"></script>
  <script src="js/password.js"></script>
</body>
</html>

// js/password.js
const password = document.getElementById("password");
const meter = document.getElementById("strength-meter");
const text = document.getElementById("strength-text");

password.addEventListener("input", () => {
  const val = password.value;
  let score = 0;
  if (val.length >= 8) score++;
  if (/[A-Z]/.test(val)) score++;
  if (/[0-9]/.test(val)) score++;
  if (/[^A-Za-z0-9]/.test(val)) score++;

  meter.value = score;

  const strength = ["Very Weak", "Weak", "Moderate", "Strong", "Very Strong"];
  text.textContent = val ? strength[score] : "";
});

<!-- README.md -->
## Password Strength Checker
The sign-up page (`signup.html`) includes a password strength meter that updates as the user types based on length, uppercase, number, and symbol presence.

```html
<input type="password" id="password">
<meter max="4" id="strength-meter"></meter>
<p id="strength-text"></p>
```

## Deployment to GitHub
Use GitHub Pages to deploy your repo. Serve locally using a live server or http-server.

```bash
npx http-server .
```
