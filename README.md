# Movie Landing Page

A responsive single-page application built with Vue.js and Vite, showcasing a dynamic movie grid using the TVMaze API, along with sections for header, hero, introduction, contact form (with validation), embedded Google Map, and footer.

## Table of Contents

* [Features](#features)
* [Demo](#demo)
* [Tech Stack](#tech-stack)
* [Prerequisites](#prerequisites)
* [Installation](#installation)
* [Project Structure](#project-structure)
* [Usage](#usage)
* [Component Overview](#component-overview)
* [Customization](#customization)
* [Future Improvements](#future-improvements)
* [License](#license)

## Features

* **Header** with logo, navigation, and hamburger menu (mobile)
* **Hero** section with configurable image, video, or slideshow
* **Introduction** section with title and descriptive text
* **Movie Grid**:

  * Loads first 3 movies on mount
  * Search bar to fetch additional movies by title
  * Remove (close) button on each movie card
* **Contact Form** with client-side validation:

  * First Name, Last Name, Email, Message fields
  * Inline error messages and red border styling
* **Embedded Google Map** showing a specified location
* **Footer** with company info, dynamic copyright, and social icons
* Fully **responsive** across desktop, tablet, and mobile

## Demo

A live demo is available at: `http://localhost:5173`

## Tech Stack

* **Framework:** Vue.js 3
* **Bundler:** Vite
* **Language:** JavaScript (ES6+)
* **Styles:** Plain CSS (Scoped styles)
* **API:** [TVMaze API](https://www.tvmaze.com/api)
* **Map:** Google Maps Embed

## Prerequisites

Make sure you have the following installed:

* Node.js (>=14.x)
* npm (>=6.x) or Yarn

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/Chethana-it/Vue-frontend.git
   ```
2. **Install dependencies**

   ```bash
   npm install
   # or
   yarn install
   ```

## Project Structure

```
movie-landing-page/
├── public/
│   └── assets/       # Images, videos & icon SVGs
├── src/
│   ├── assets/       # (optional) imported assets
│   ├── components/   # Vue components
│   │   ├── Header.vue
│   │   ├── Hero.vue
│   │   ├── Intro.vue
│   │   ├── MovieGrid.vue
│   │   ├── Contact.vue
│   │   └── Footer.vue
│   ├── App.vue       # Root component
│   └── main.js       # Application entry point
├── index.html        # App shell
├── package.json      # Project metadata & scripts
├── vite.config.js    # Vite configuration
└── README.md         # Project documentation
```

## Usage

* **Start development server**

  ```bash
  npm run dev
  ```

  Open `http://localhost:5173` in your browser.

* **Build for production**

  ```bash
  npm run build
  ```

* **Preview production build**

  ```bash
  npm run preview
  ```

## Component Overview

* **Header.vue**: Site header with logo, navigation links, and responsive hamburger menu.
* **Hero.vue**: Displays a hero image or video. Can be extended into a slideshow.
* **Intro.vue**: Static introduction text section.
* **MovieGrid.vue**:

  * Fetches initial movies by ID on mount.
  * Includes search functionality to add more movies.
  * Cards display image, title, summary, and remove button.
* **Contact.vue**:

  * Renders a form with client-side validation.
  * Shows inline errors and resets form on successful submission.
  * Embeds Google Map iframe for location.
* **Footer.vue**: Site footer with company info, social icons, and dynamic year.

## Customization

* **Hero section**: Swap `src/assets/hero.jpg` or update `Hero.vue` to use video/slideshow.
* **Map location**: Replace the iframe `src` URL in `Contact.vue` with your own embed code.
* **API endpoints**: Change `MovieGrid.vue` fetch URLs to use a different movie API if desired.

## Future Improvements

* Add CSS animations or transitions using GreenSock (GSAP).
* Implement RTL (right-to-left) language support.
* Improve accessibility to WCAG AA standards.
* Split form validation into reusable composables.
* Add Vue Router for page navigation.

## License

This project is released under the [MIT License](LICENSE).
