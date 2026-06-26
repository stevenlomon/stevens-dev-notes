# What and Why (big picture + mental model)

## Prerequisite Checklist

Before diving into React, I feel that it is recommended to have a somewhat strong grasp of the JavaScript fundamentals and feel comfortable with the language as a whole. React abstracts away a lot for us but it still needs us to write in JavaScript (or TypeScript).  
***<mark>React doesn't change JavaScript; it leverages its advanced behaviors.</mark>***  
Some areas in particular (that are used extensively in React) to brush up on in order to make learning and understanding React as smooth sailing as possible:  
**Core:**
* **Immutability:**   
In Vanilla JS, we do a lot of modifying arrays and objects in place: `myArray[0] = 5` or `cat.name = 'Figaro'`. This is mutating data directly.  
**In React, we don't do this. We *never* write something like `state[0] = x` or `state.value = y`.**   
Instead, we need to get comfortable with **non-mutating** methods and the Spread operator, see the next two points.
* **Array (and Object) methods:** To adhere to the central React principle of Immutability, we use use array and object methods that return **brand-new copies** of the original. The reason why is a deep dive but the short answer is that React detects changes and knows when to re-render the page by comparing old memory references to new memory references (our new arrays/objects).  
  The two most commonly used array methods are `.map()` and `.filter()`.
* The **Spread Operator (`...`):** Is used very often for copying and updating objects cleanly inside state modifiers for the same reason we use array and object methods rather than direct variable assignment. **Instead of `person.firstName = 'Alex'`, somewhere in the code we would have `return {...person, firstName: 'Alex'}`**
* **Destructuring:** Is used very often with props (coming up later in this doc). Essential for cleanly unpacking elements from arrays and objects. 
* **Arrow Functions and Callback Functions:** Arrow functions are used very often as props for passing callback functions without losing context.

**Deep dives:**
* **Asynchronous JavaScript**
* **The Event Loop**
* **Closures**
* **Lexical Scope**
* **Value vs. Reference Types**
* **State Batching / Asynchronous State Updates**

## What is React?

In one clean sentence:   
**React is a JavaScript library used for building user interfaces using a component-based philosophy (where JavaScript generates the structure *and* manipulates it) rather than a traditional document-based one (where HTML structures the page and JavaScript is only used to make it interactive)**  

Some of my own confusions and curiosities cleared up:
* **"Is it a library or a framework?"** It is a **library**. Next.js is an example of a framework. It touches the application architecture; routing, data-fetching, server management etc etc.   
**React focuses on one thing: <mark>translating state into UI</mark>**
	* Furthermore; **Next.js is built on top of React.** So the natural Full Stack learning progression goes JavaScript -> React -> Next.js (when being somewhat comfortable with TypeScript and more importantly Backend fundamentals through libraries like Express).   
  Since Next.js is built on top of React, **any time spent learning and understanding React is not wasted since it builds into Next.js, just like any time spent learning and understanding JavaScript is not wasted since it builds into React.**
* **"Is it built "on top" of JavaScript?"** No. React **is** pure JavaScript. Under the hood, a JSX file is transformed into JavaScript by a build tool.
* **"Does it need a build tool like Vite?"** Technically, no, but practically, **yes**. Browsers do not understand JSX out of the box. A build tool compiles JSX into standard JavaScript, optimizes our assets, bundles dependencies, and ensures the application runs at maximum efficiency when it reaches the browser.

## Why React?

**No more querySelectors.** This alone is almost enough to never touch Vanilla JavaScript and commit to learning React haha. But it is part of one of the biggest main benefits of using React.  
In Vanilla JavaScript, we write a lot of ***imperative*** code; step-by-step instructions telling the browser exactly *how* to modify the screen. Lines upon lines like `document.getElementById('start-btn').textContent = "Lock In"`).  
In React, we write ***declarative*** code; we describe exactly what the screen *should* look like based on the current state, and React figures out how to update the display.  
***<mark>Declarative flow, not imperative force.</mark>***  
This was my personal mantra and mental anchor that I came up with when trying to learn React on my own in 2024 (I gave up haha) and it has only been solidified when learning it properly now in 2026 thanks to my Full Stack studies and building proper projects.

Two other main benefits include:
*  **Centralized State:** Instead of scattering bits of memory across HTML data attributes and random variables, state lives in dedicated and protected "boxes" (using `useState` / `useReducer`).
* **Component Architecture:** The interface is broken down into isolated, self-contained chunks. If an element breaks, the bug is isolated to that specific file instead of polluting a massive, monolithic script.

### **What is abstracted away?**
**The entire DOM Tree** is completely abstracted away from us. We no longer query elements, manually append children, or directly alter CSS properties. React maintains an internal lightweight representation of the interface. When state changes, it calculates the most efficient update and handles the heavy lifting of real DOM manipulation entirely in the background.

### Are there merits of NOT using React?
Maybe if we are building something ultra-lightweight or completely static like a personal blog. Or if we have a tiny interactive element that requires just a few lines of code, setting up a full build tool chain introduces unnecessary complexity and asset overhead for the browser to download.
