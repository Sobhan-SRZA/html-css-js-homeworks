# Homework-3: Simple E-Commerce Website 📦

![Project Banner](https://via.placeholder.com/1200x300?text=Homework-3+E-Commerce+Site)  
*(Note: Replace this placeholder with an actual banner image if available.)*

## 📖 Overview
Welcome to **Homework-3**, a beginner-level e-commerce website project built as part of a web development lesson (Lesson 12 Homework). This project demonstrates basic front-end skills using HTML, CSS (with Sass), and JavaScript. It features user authentication (login/signup with CAPTCHA), product listing, a shopping cart, and a simple responsive layout.

The site simulates an online store where users can sign up, log in, browse products, add items to a cart, and view totals. No backend or real database is involved—everything is handled client-side with in-memory data.

**Key Features** 🚀:
- User registration and login with validation and CAPTCHA for security.
- Product catalog with add-to-cart functionality.
- Dynamic shopping cart that updates in real-time.
- Responsive design for mobile and desktop.
- Sass for modular CSS styling.
- GitHub Pages deployment workflow.

This project is ideal for learning front-end basics, form handling, DOM manipulation, and CSS animations.

## 🛠️ Tech Stack
- **HTML5**: Structure and content.
- **CSS3/Sass**: Styling with variables, mixins, and responsive media queries.
- **JavaScript (ES6+)**: Logic for forms, validation, CAPTCHA, and cart management.
- **jQuery**: Included via dependencies (though minimally used in code).
- **Node.js/NPM**: For Sass compilation and development scripts.
- **GitHub Actions**: For static deployment to GitHub Pages.

## 📂 Project Structure
Here's the file structure of the project:

```
Homework-3/
├── .github/
│   └── workflows/
│       └── static.yml          # GitHub Actions workflow for deploying to GitHub Pages 🚀
├── images/                     # Folder for icons and product images (e.g., icon.png, کفش.png) 🖼️
├── sass/
│   ├── _container.scss         # Styles for main container components 🎨
│   ├── _default.scss           # Default styles and resets
│   ├── _mixin.scss             # Sass mixins for reusable code (e.g., forum, products)
│   ├── _responsive.scss        # Media queries for responsiveness 📱
│   ├── _variuable.scss         # Sass variables for colors and themes
│   └── main.scss               # Main Sass entry point importing all partials
├── .gitignore                  # Ignores node_modules, package-lock.json, etc. 🗑️
├── index.html                  # Main HTML file with structure 🏗️
├── package.json                # NPM dependencies and scripts 📦
├── README.md                   # Original project README with contact info 📄
├── script.js                   # JavaScript logic for interactivity ⚙️
├── style.css                   # Compiled CSS from Sass
└── style.css.map               # Source map for CSS debugging 🔍
```

## ⚙️ Setup and Installation
1. **Clone the Repository** 📥:
   ```
   git clone https://github.com/your-username/Homework-3.git
   cd Homework-3
   ```

2. **Install Dependencies** 📦:
   ```
   npm install
   ```
   - This installs Sass (devDependency) and jQuery (dependency).

3. **Compile Sass** 🎨:
   - Run once: `npm run compile` (compiles `sass/main.scss` to `style.css`).
   - Watch mode: `npm run watch` (auto-compiles on changes).

4. **Run Locally** 🌐:
   - Open `index.html` in a browser (no server needed, as it's static).

5. **Deploy to GitHub Pages** 🚀:
   - Push to `main` branch—the workflow in `.github/workflows/static.yml` handles deployment automatically.

## 📜 Commands and Scripts
From `package.json`:

- `npm run watch` 👀: Watches Sass files and auto-compiles to CSS. Ideal for development.
- `npm run compile` 🔨: Compiles Sass once without watching.
- `npm run test` ❌: Placeholder script (echoes an error; no actual tests implemented).

These scripts use Sass CLI for CSS generation.

## ✨ Features and Usage
### 1. **User Authentication** 🔐
   - **Signup/Login Form**: Toggle between modes via a link. Includes live validation for name, email, password, and CAPTCHA.
   - **CAPTCHA**: Generates a 5-digit random code for bot protection.
   - **Validation Rules**:
     - Name: Required (text).
     - Email: Required, valid format (regex: `/^[^\s@]+@[^\s@]+\.[^\s@]+$/`).
     - Password: Required, minimum 6 characters.
     - CAPTCHA: Required, exactly 5 digits, matches generated code.
   - After successful login/signup, displays a welcome message and hides the form.

### 2. **Product Catalog** 🛍️
   - Displays 5 hardcoded products (e.g., shoes, bag, watch, phone, bracelet) with images, names, and prices.
   - Users must log in to add items to cart (alerts if not logged in).

### 3. **Shopping Cart** 🛒
   - Adds products to an in-memory cart array.
   - Updates UI dynamically: Shows cart items and total price (formatted with `toLocaleString()`).
   - No removal or persistence—resets on page reload.

### 4. **About Us Section** ℹ️
   - Static lorem ipsum text in Persian.

### 5. **Footer** 🦶
   - Links to sections, copyright notice, and duplicate nav links for symmetry.

## 🔑 Key JavaScript Components
The core logic is in `script.js`, encapsulated in a `Main` class instantiated on DOM load.

### **Data Structures (In-Memory "Databases")** 💾
No real database; uses arrays/objects for storage. Here's a breakdown with samples and types:

1. **Products Array** (Array of Objects):
   - Sample: 
     ```json
     [
       { "name": "کفش", "price": 829500 },  // Type: {name: string, price: number}
       { "name": "کیف", "price": 402000 },
       // ... (5 items total)
     ]
     ```
   - Usage: Rendered in product grid; added to cart.

2. **Users Array** (Array of Objects):
   - Sample (initial):
     ```json
     [
       { "name": "سبحان", "email": "sobhan@gmail.com", "password": "123456789" }  // Type: {name: string, email: string, password: string}
     ]
     ```
   - Usage: Stores registered users. New users pushed during signup.

3. **Cart Array** (Array of Objects, instance property):
   - Sample (after adding items):
     ```json
     [
       { "name": "کفش", "price": 829500 },  // Same type as products
       // ...
     ]
     ```
   - Usage: Tracks selected products; used for total calculation (`reduce` for sum).

4. **LoggedInUser** (Object or Null):
   - Sample: `{ "name": "سبحان", "email": "sobhan@gmail.com", "password": "123456789" }`  // Type: Object or null
   - Usage: Tracks current user session.

5. **CurrentCaptcha** (String):
   - Sample: `"12345"`  // Type: string (5 digits)
   - Usage: Generated randomly; validated on submit.

### **Frequently Used Functions** 🛠️
- **genCaptcha(size = 5)**: Generates random 5-digit string.  
  *Usage*: Called on form render for security.

- **validateField(input, type)**: Live validation for inputs (text, email, password, captcha).  
  *Usage*: Attached to 'input' event; shows errors/success.

- **login() / signup()**: Handles form submission, validation, CAPTCHA check, and user management.  
  *Usage*: onclick handlers; pushes to users array or authenticates.

- **addToCart(product)**: Pushes product to cart and calls `updateCart()`.  
  *Usage*: On product button click (after login check).

- **updateCart()**: Renders cart items and total price.  
  *Usage*: After adding items; uses `map` and `reduce`.

- **renderForm(isLogin = false)**: Generates HTML for login/signup form dynamically.  
  *Usage*: Toggles form mode.

- **renderProducts()**: Maps products to HTML grid.  
  *Usage*: On page load.

- **attachEvents()**: Adds event listeners for form toggle and product clicks.  
  *Usage*: In constructor.

### **Command/Function Templates** 📝
- **Form Submission Template**:
  ```javascript
  // Example: Signup
  const userData = { name: nameInput.value, email: emailInput.value, password: passwordInput.value };
  if (validationsPass && captchaMatches) {
    users.push(userData);
    loggedInUser = userData;
    showSuccess('Success!');
  }
  ```

- **Cart Update Template**:
  ```javascript
  this.cart.push(product);
  cartItems.innerHTML = this.cart.map(item => `<div>...</div>`).join('');
  totalPrice.textContent = `Total: ${this.cart.reduce((sum, item) => sum + item.price, 0).toLocaleString()} تومان`;
  ```

## 🐛 Known Issues & Improvements
- No password hashing (insecure for real use).
- Cart resets on reload—add localStorage for persistence.
- Limited products/users—expand with more data.
- Minimal jQuery usage—could be removed for vanilla JS.
- Add logout button and cart removal.

## 🤝 Contributing
Fork the repo, make changes, and submit a PR! Issues welcome. 🌟

## 📧 Contact
See the original README.md for social links (Telegram, Instagram, etc.).

## 📄 License
ISC (as per package.json). All rights reserved © 1404 (2025 Gregorian).