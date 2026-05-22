# Homework-5: Personal Portfolio Website

![Portfolio Preview](images/profile.jfif) <!-- Assuming this is a preview image; replace if needed -->

## 📖 Overview

Welcome to **Homework-5**, a simple yet elegant static portfolio website showcasing my personal profile, biography, and key projects. This project is built using pure HTML and CSS, with no JavaScript or backend dependencies. It's designed to be lightweight, responsive, and easy to deploy on platforms like GitHub Pages.

The website highlights:
- My personal details (name, age, interests).
- A selection of my Discord bot projects (Padio, Ticker Boy, Pc Bot).
- SEO-friendly meta tags for better visibility.
- Smooth loading animations and hover effects for an engaging user experience.

This documentation provides a complete guide to the source code, structure, features, and deployment. It's intended for developers, contributors, or anyone interested in forking and customizing the project.

🚀 **Live Demo**: [View on GitHub Pages](https://srza.ir/) (or your deployed URL).

## 🗂️ Project Structure

The project follows a straightforward static site structure. Here's the file tree:

```
Homework-5/
├── .gitattributes          # Git configuration for line endings
├── .github/
│   └── workflows/
│       └── static.yml      # GitHub Actions workflow for deploying to GitHub Pages
├── images/                 # Folder for all images (not included in source but referenced)
│   ├── icon.png            # Favicon
│   ├── og-image.jpg        # Open Graph image for social sharing
│   ├── padio.png           # Project image for Padio
│   ├── pc-bot.png          # Project image for Pc Bot
│   ├── profile.jfif        # Profile picture
│   └── ticker-boy.webp     # Project image for Ticker Boy
├── index.html              # Main HTML file (entry point)
└── style.css               # CSS stylesheet for layout, animations, and responsiveness
```

- **Total Files**: 6 (including workflow and attributes).
- **Dependencies**: None (pure HTML/CSS).
- **Build Tools**: GitHub Actions for deployment.

## 📄 File Explanations

### 1. `.gitattributes`
- **Purpose**: Ensures consistent line endings (LF normalization) across platforms for text files.
- **Content Summary**:
  ```
  # Auto detect text files and perform LF normalization
  * text=auto
  ```
- **Key Features**: Prevents Git from mangling file formats during commits.

### 2. `index.html`
- **Purpose**: The core HTML structure of the portfolio. It includes the profile card, project showcases, meta tags for SEO and Open Graph, and links to CSS and images.
- **Key Sections**:
  - **Head**: Meta tags for charset, viewport, title, description, keywords, and Open Graph properties (for social sharing).
  - **Body**:
    - **Profile Card**: Displays profile image, name (linked to GitHub), and biography.
    - **Projects Section**: Grid of project cards with images, names (linked to GitHub repos), and descriptions.
- **Classes Used**: 
  - `loading` for animation triggers.
  - `image-hover`, `image-shadow` for image effects.
  - `text-hover`, `text-link` for link styling.
- **No Functions or Scripts**: This is static HTML only.
- **Sample Snippet** (Profile Card):
  ```html
  <div class="profile-card loading">
      <img class="profile-card--image image-hover image-shadow loading" src="images/profile.jfif" alt="Sobhan-SRZA profile image">
      <h1 class="profile-card--name loading"><a href="https://github.com/Sobhan-SRZA" class="text-hover text-link">Sobhan-SRZA (mr.sinre)</a></h1>
      <p class="profile-card--description loading">Hello, I'm Sobhan... [biography text]</p>
  </div>
  ```

### 3. `style.css`
- **Purpose**: Defines all styles, animations, and responsive layouts.
- **Key Components**:
  - **Global Resets**: `*::after, *::before, * { margin: 0; padding: 0; box-sizing: border-box; }` for consistent layout.
  - **Body Styles**: Dark background, flex layout for centering content.
  - **Hover Effects**:
    - `.image-hover`: Transitions shadow on hover.
    - `.text-hover`: Changes color on hover.
  - **Animations**:
    - `@keyframes loading`: Scales and fades in elements from 0.5 scale and 0 opacity.
  - **Profile Card**: Grid layout with areas for image, name, and description.
  - **Projects Section**: Flex row for project cards, switches to column on mobile.
  - **Responsive Media Query**: `@media (max-width: 768px)` adjusts layouts for smaller screens.
- **No Functions**: CSS is declarative; no procedural code.
- **Sample Snippet** (Loading Animation):
  ```css
  .loading {
      animation: loading 2s ease-in-out both;
  }
  @keyframes loading {
      0% { transform: scale(0.5); opacity: 0; margin-top: 30px; }
      50% { transform: scale(1); opacity: 1; }
      80% { opacity: .9; }
      100% { transform: translateX(0); }
  }
  ```

### 4. `.github/workflows/static.yml`
- **Purpose**: Automates deployment to GitHub Pages on pushes to the `main` branch or manual triggers.
- **Key Steps**:
  - Checkout code.
  - Setup Pages.
  - Upload artifact (entire repo).
  - Deploy to Pages.
- **Permissions**: Read contents, write Pages, write ID token.
- **Concurrency**: Allows only one deployment at a time but doesn't cancel in-progress ones.
- **Sample Snippet**:
  ```yaml
  name: Deploy static content to Pages
  on:
    push:
      branches: ["main"]
    workflow_dispatch:
  # ... [rest of the workflow]
  ```

## ✨ Features

- **Responsive Design** 📱: Adapts to mobile and desktop views using media queries. On screens <768px, projects stack vertically, and profile centers text.
- **Loading Animations** 🌟: Elements fade in and scale up for a smooth entrance.
- **Hover Interactions** 🖱️: Images glow with shadows; links change color.
- **SEO Optimization** 🔍: Meta tags for description, keywords, and Open Graph for better sharing on social media.
- **Project Showcases** 🔗: Links to GitHub repos for my Discord bots:
  - **Padio** 🎵: Radio bot for Discord with online stations.
  - **Ticker Boy** 🎟️: Professional ticket system with dashboards, buttons, and slash commands.
  - **Pc Bot** 🤖: Multi-feature bot including ticketing, giveaways, music, backups, moderation, fun, economy, and more.
- **No Database or Backend**: Fully static; no data storage, commands, or dynamic features.
- **Theme**: Green-toned (e.g., `rgb(83, 189, 154)`) with dark background for a modern look.

⚠️ **Note on Bots**: This portfolio references my Discord bot projects, but this source code is for the website only. For bot-specific docs (commands, features), check their respective GitHub repos linked in the HTML. This project has no bot commands, databases, or runtime functions as it's static HTML/CSS.

## 🛠️ Commonly Used Patterns

- **CSS Classes**: Reusable for hover (`image-hover`, `text-hover`) and shadows (`image-shadow`).
- **Grid/Flex Layouts**: Profile uses CSS Grid; projects use Flexbox.
- **No Functions or Templates**: No JavaScript; all "templates" are hardcoded HTML structures.
- **No Databases**: This static site doesn't store or use any data. No samples or types available (N/A).

## 🚀 Deployment Guide

1. **Fork the Repo** 🍴: Clone to your machine.
2. **Add Images** 🖼️: Place required images in the `images/` folder.
3. **Commit & Push** 📤: Push to `main` branch.
4. **Enable GitHub Pages** ⚙️: In repo settings > Pages, select `main` branch and `/ (root)`.
5. **Workflow Runs Automatically**: Deploys on push via `.github/workflows/static.yml`.

**Commands for Local Development**:
- No build commands needed (static).
- Preview locally: Open `index.html` in a browser.
- Git Commands:
  ```
  git clone <your-repo-url>
  git add .
  git commit -m "Update portfolio"
  git push origin main
  ```

## 🤝 Contributing

Feel free to fork and submit PRs! Suggestions: Add dark mode toggle, more projects, or JavaScript for interactivity.

## 📝 License

MIT License. Free to use and modify.

❤️ Made by Sobhan-SRZA (Mr. Sinre) in 2025.