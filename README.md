# 🎬 Vue.js + HTML5 + CSS Movie Website

A fully responsive movie-themed website built using **Vue.js**, **HTML5**, and **Vanilla CSS**, without any external UI libraries or frameworks. Designed for cross-browser compatibility and mobile responsiveness.

---

## 📌 Features

### 🧱 Tech Stack

- ✅ Vue.js (No React, Angular, etc.)
- ✅ HTML5 (Semantic markup)
- ✅ CSS / SASS (No Tailwind, Bootstrap)
- ✅ Vanilla JavaScript (No jQuery, TypeScript)
- ✅ Movie data via [TV Maze API](https://www.tvmaze.com/api)

---

## 🚧 Sections Built

### A. Header

- 📌 Logo aligned based on screen size
- 📌 Navigation menu with hover effects
- 📌 Hamburger menu for smaller devices (toggle open/close)

### B. Hero Section

- 🖼️ Large hero image
- 🎞️ (Optional) Slideshow or replace with video background

### C. Introduction

- ✍️ Styled title and paragraph as per design

### D. Movie Grid

- 🔹 Title and movie list
- 🔹 Fetch movies via API or hardcoded from API response
- 🔹 Each movie includes:
  - Poster image
  - Title
  - Description
  - ❌ Close button to remove the movie card
- 🔍 Search input to dynamically add new movies to the grid

### E. Contact & Map

- 📄 Form Fields:
  - First Name *(required)*
  - Last Name *(required)*
  - Email *(required, must be valid)*
  - Message *(required)*
- ✅ JavaScript form validation with red border + error messages
- 📍 Embedded Google Map: [Amadeus HQ](https://goo.gl/maps/5sW9xsCNvByPnxXE9)
- 💬 Optional: Alert on submission showing form data (no DB/email)

### F. Footer

- 🏢 Address & title
- 🌐 Social icons using provided assets
- 📅 Copyright:
  - Dynamic year display using JavaScript

---

## ⚙️ Optional Enhancements

- 🎨 CSS animations or GreenSock
- 💡 RTL (Right to Left) support
- ♿ WCAG Level A / AA accessibility
- 🔧 Modular structure using Vue components
- 📦 NPM for dependency management
- ⚡ Vite / Webpack for bundling

---

## 📁 Folder Structure

```
/public              # Static files
/src
  /assets            # Images, videos
  /components        # Vue components (Header, Footer, MovieCard, etc.)
   App.vue
  main.js
README.md
vite.config.js       # Vite config
package.json
```

---

## 🛠️ Getting Started

### 1️⃣ Clone the Repo

```bash
git clone https://github.com/hasharas/vue-movie
cd your-repo-name
```

### 2️⃣ Install Dependencies

```bash
npm install
# or
yarn install
```

### 3️⃣ Run Development Server

```bash
npm run dev
# or
yarn dev
```

### ✅ App will run at:

```
http://localhost:5173
```

---

## 📜 License

This project is licensed under the MIT License.

---

## 👨‍💻 Author

- **Your Name**
- GitHub: https://github.com/hasharas/vue-movie
- Email: hasharamsankalpam@gmail.com
