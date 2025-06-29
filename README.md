# Reviews Project - React Fundamental Project 3

---

<img width="637" alt="Screenshot 2025-02-09 at 02 12 20" src="https://github.com/user-attachments/assets/510475f3-12ea-43bd-a611-35a1142d3ebf" />

---

## Project Summary

The **Reviews Project** is a beginner-friendly React application designed to teach core React concepts through a hands-on example. The project displays user reviews, allowing users to browse through different reviewers, view a random review, and understand how data flows in a React app. It's ideal for those new to React who want to learn about state management, component structure, props, and simple UI interactions.

- **Live-Demo:** [https://reviews-arnob.netlify.app/](https://reviews-arnob.netlify.app/)

---

## Table of Contents

1. [Project Summary](#project-summary)
2. [Features](#features)
3. [Project Structure](#project-structure)
4. [Technologies Used](#technologies-used)
5. [Setup & Installation](#setup--installation)
6. [Walkthrough & Instructions](#walkthrough--instructions)
7. [Key Components & Code Examples](#key-components--code-examples)
8. [Concepts & Keywords](#concepts--keywords)
9. [Conclusion](#conclusion)

---

## Features

- **Display Reviews**: Shows user reviews with name, job, image, and review text.
- **Navigation**: "Next" and "Previous" buttons to browse through different reviews.
- **Random Review**: Button to jump to a random review.
- **Interactive UI**: Clean, beginner-friendly interface.
- **Educational Comments**: Code structured for learning and easy understanding.

---

## Project Structure

Here’s a typical file structure for this project:

```
Reviews--React-Fundamental-Project-3/
├── public/
│   └── index.html
├── src/
│   ├── components/
│   │   └── Review.jsx
│   ├── data.js
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
├── package.json
├── README.md
└── ...
```

- **src/data.js**: Contains the array of review objects (name, job, image, text).
- **src/components/Review.jsx**: Main component displaying a single review and navigation buttons.
- **src/App.jsx**: Main application component, manages state and renders `Review`.
- **src/index.css**: Basic styling.

---

## Technologies Used

- **React**: UI library for building interactive interfaces.
- **JavaScript (ES6+)**: Core language.
- **Vite** or **Create React App**: For project bootstrapping and local development.
- **React Icons**: For UI icons (optional).

---

## Setup & Installation

Follow these steps to run the project locally:

1. **Clone the repository:**
   ```sh
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Install dependencies:**
   ```sh
   npm install
   ```

3. **Run the development server:**
   ```sh
   npm run dev
   ```
   > If using Create React App, use `npm start`.

4. **Open your browser:**  
   Visit `http://localhost:5173` or the port mentioned in your terminal.

---

## Walkthrough & Instructions

### 1. Explore Data

Check the `src/data.js` file. It exports an array of objects, each representing a review:
```js
const reviews = [
  {
    id: 1,
    name: 'John Doe',
    job: 'Web Developer',
    image: 'https://...',
    text: 'John’s review here...'
  },
  // more reviews
];
export default reviews;
```
---

### 2. Import Reviews

In `App.jsx`, import the reviews data:
```js
import reviews from './data';
```
---

### 3. Setup State Value (Index)

Use React's `useState` to track which review is currently displayed:
```js
const [index, setIndex] = useState(0);
```
---

### 4. Render the First Person

Display the review at the current index:
```js
const { name, job, image, text } = reviews[index];
```
---

### 5. Prev, Next, and Random Buttons

Add buttons to cycle through the reviews and select a random review:
```js
<button onClick={prevPerson}>Prev</button>
<button onClick={nextPerson}>Next</button>
<button onClick={randomPerson}>Random</button>
```
Example handlers:
```js
const prevPerson = () => {
  setIndex((oldIndex) => (oldIndex - 1 + reviews.length) % reviews.length);
};
const nextPerson = () => {
  setIndex((oldIndex) => (oldIndex + 1) % reviews.length);
};
const randomPerson = () => {
  let randomIndex = Math.floor(Math.random() * reviews.length);
  setIndex(randomIndex);
};
```
---

### 6. Using React Icons (Optional)

To add icons:
```sh
npm install react-icons --save
```
Example usage:
```js
import { FaBeer } from "react-icons/fa";
<FaBeer />
```
---

## Key Components & Code Examples

### `Review.jsx`

```jsx
import React from 'react';

const Review = ({ name, job, image, text, onPrev, onNext, onRandom }) => (
  <article>
    <img src={image} alt={name} />
    <h4>{name}</h4>
    <p>{job}</p>
    <p>{text}</p>
    <div>
      <button onClick={onPrev}>Prev</button>
      <button onClick={onNext}>Next</button>
      <button onClick={onRandom}>Random</button>
    </div>
  </article>
);

export default Review;
```
---

### `App.jsx` (Simplified)

```jsx
import React, { useState } from 'react';
import reviews from './data';
import Review from './components/Review';

function App() {
  const [index, setIndex] = useState(0);
  const prevPerson = () => setIndex((i) => (i - 1 + reviews.length) % reviews.length);
  const nextPerson = () => setIndex((i) => (i + 1) % reviews.length);
  const randomPerson = () => setIndex(Math.floor(Math.random() * reviews.length));

  return (
    <main>
      <Review
        {...reviews[index]}
        onPrev={prevPerson}
        onNext={nextPerson}
        onRandom={randomPerson}
      />
    </main>
  );
}

export default App;
```
---

## Concepts & Keywords

- **State Management**: Using `useState` to store and change the index of the current review.
- **Props**: Passing review data and handlers to components.
- **Component Structure**: Splitting UI into reusable pieces.
- **Event Handling**: Functions for navigation and randomization.
- **Modulus Operator `%`**: To loop through reviews circularly.
- **Array Methods**: Accessing and rendering data.

---

## Conclusion

This project is an excellent starting point for React newcomers. It demonstrates how to manage state, handle events, and pass data between components. By building and experimenting with this app, you'll gain foundational skills necessary for more advanced React projects.

Feel free to experiment by adding more features, such as editing reviews, fetching reviews from an API, or improving the UI with CSS frameworks. Happy coding!

---
