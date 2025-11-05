# Product list with cart — Frontend Mentor solution

A clean, responsive product list with a client-side cart built for the Frontend Mentor "Product list with cart" challenge.

This repository is a lightweight HTML/CSS/JavaScript solution that uses a local `data.json` as the product source and implements add/remove, quantity controls, a confirmation modal, and a "Start New Order" reset flow.

## Table of contents

- [Demo / Screenshot](#demo--screenshot)
- [Overview](#overview)
- [Features](#features)
- [Built with](#built-with)
- [Data format](#data-format)
- [Getting started](#getting-started)
- [Usage](#usage)
- [Customizing the product data](#customizing-the-product-data)
- [Accessibility & testing notes](#accessibility--testing-notes)
- [Contributing](#contributing)
- [Author](#author)
- [License](#license)

## Demo / Screenshot

If you want to preview quickly, open `index.html` in a browser or run a simple local server (instructions below).

This is a project screenshot to `./screenshot.png`

![](./screenshot.png)

## Overview

This project solves the Frontend Mentor challenge by providing a responsive product listing and a cart UI. Product data is loaded from `data.json`, each product includes responsive images, a name, category, id, and price.

The app is intentionally simple and framework-free so it can be used as a learning example or a small UI component to embed in other projects.

## Features

- Add items to the cart
- Increment/decrement quantity per product
- Remove items from the cart
- Order confirmation modal when clicking "Confirm Order"
- "Start New Order" button resets cart and selections
- Responsive layout and responsive images (mobile/tablet/desktop)
- Keyboard and focus states for interactive elements

## Built with

- HTML5
- CSS (flexbox, grid, custom properties)
- JavaScript (ES6 modules / DOM APIs)
- Static JSON data (`data.json`) for products

No build step or external dependencies are required — just open the files in a browser.

## Data format

Product data is stored in `data.json` at project root. Each product uses this shape:

```json
{
  "image": {
    "thumbnail": "./assets/images/...",
    "mobile": "./assets/images/...",
    "tablet": "./assets/images/...",
    "desktop": "./assets/images/..."
  },
  "id": 1,
  "name": "Waffle with Berries",
  "category": "Waffle",
  "price": 6.5
}
```

- `image` contains paths for responsive images (thumbnail, mobile, tablet, desktop)
- `id` is a unique numeric identifier used by the cart
- `name` and `category` are display strings
- `price` is a number (currency shown in the UI)

When you edit or add products, ensure image paths and unique `id` values are correct.

## Getting started

Requirements: a modern browser. Optional: Python or Node.js if you want a local HTTP server.

1.  Clone the repo or download the ZIP

```powershell
git clone https://github.com/kingjenathe7th/product-list-with-cart-main.git
cd product-list-with-cart-main
```

2a. Open directly (simplest)

Open `index.html` in your browser (double-click or File → Open).

2b. Or run a quick local server (recommended for consistent behavior)

Using Python 3 (PowerShell):

```powershell
python -m http.server 8000
# then open http://localhost:8000 in your browser
```

Using Node.js http-server (if Node is installed):

```powershell
npx http-server -c-1
# then open the provided local URL
```

## Usage

- Browse products and click the "Add to cart" button (or equivalent control) to add an item.
- Use the + / − controls in the cart to change quantities.
- Remove an item by clicking the trash/remove button in the cart.
- Click "Confirm Order" to show a confirmation modal.
- Click "Start New Order" to clear the cart and reset selections.

The implementation stores cart state in JavaScript runtime (no persistence). If you'd like persistence, consider adding localStorage support.

## Customizing the product data

- Edit `data.json` to add, remove, or change products. Maintain the same fields (`image`, `id`, `name`, `category`, `price`).
- Put image assets under `assets/images/` and update paths in `data.json`.

Example: add a new product object to the JSON array with a new `id` and image entries.

## Accessibility & testing notes

- Interactive elements include visible focus styles and ARIA-friendly semantics where applicable.
- Test keyboard navigation (Tab / Enter / Space) and screen-reader labels if you plan to expand the app.

## Contributing

Small improvements are welcome. Typical contributions:

1.  Fork the repo
2.  Create a feature branch
3.  Open a pull request describing your changes

If you add a larger feature (persistence, user accounts, payments), open an issue first so we can discuss the approach.

### What I learned

I learnt Operating on the DOM with javascript.I also learnt how to work with JSON files.

To see how you can add code snippets, see below:

```html

```

```css
.modal-container {
  background-color: rgba(0, 0, 0, 0.3);
  position: fixed;
  inset: 0;
  z-index: 999;
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 50px;
  opacity: 0;
  pointer-events: none;
}
```

```js
const initApp = () => {
  //get data from the json
  fetch("./data.json")
    .then((response) => response.json())
    .then((data) => {
      productsData = data.reduce((acc, product) => {
        acc[product.id] = product;
        return acc;
      }, {});
      console.log(productsData);
      addDataToHTML();

      if (localStorage.getItem("cart")) {
        carts = JSON.parse(localStorage.getItem("cart"));
        addToCartHtml();
        reflectCartState();
      }
    })
    .catch((error) => console.error("Error fetching data:", error));
};
```

If you want more help with writing markdown, we'd recommend checking out [The Markdown Guide](https://www.markdownguide.org/) to learn more.

**Note: Delete this note and the content within this section and replace with your own learnings.**

### Continued development

I will Dive deep into JS and check out OOP.

**Note: Delete this note and the content within this section and replace with your own plans for continued development.**

### Useful resources

- [Example resource 1](https://www.example.com) - This helped me for XYZ reason. I really liked this pattern and will use it going forward.
- [Example resource 2](https://www.example.com) - This is an amazing article which helped me finally understand XYZ. I'd recommend it to anyone still learning this concept.

**Note: Delete this note and replace the list above with resources that helped you during the challenge. These could come in handy for anyone viewing your solution or for yourself when you look back on this project in the future.**

## Author

- Website - [Jenakumo Emmanuel](https://jenacodes.vercel.app)
- Twitter - [@kingjenathe7th](https://www.twitter.com/kingjenathe7th)
