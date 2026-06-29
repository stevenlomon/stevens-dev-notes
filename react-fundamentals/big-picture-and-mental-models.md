# The Big Picture and Mental Models

This is a follow-up pre deep dive document to [What and Why](what-and-why.md), it would serve you to read that one first. 

## The Big Picture (and how it all connects together)
At the very core, heart and center of React are <mark>**Components**</mark> and <mark>**State Management**</mark>.  
Every line of code we write is in some way either:
* _updating state_
* _describing a component’s layout_, or 
* _defining how a component transforms based on that state_.  

**Component Hierarchy** describes _how components connect and relate to each other_ in a tree structure. There are parent components and child components.  

Data is passed *downward* from Components to their children in what we call **props**. The exploration of these naturally leads to two core JavaScript concepts and how they're primarily used in React: 
* **Object Destructuring:** When we unpack the prop object passed from a parent to a child.
* **Callback Functions:** Functions passed down from a parent that a child component can fire. This is the foundation of a core React principle called **Lifting State Up**.

To track data that changes over time, we use **Hooks**. The most common hook in all of React is one that is directly tied to state management: **`useState`**. When state management becomes a tangled web of interdependent changes is when we need to look into Complex State Management and `useState`'s big brother `useReducer`. Other hooks include `useEffect`, `useContext`, `useRef` etc. etc. 

How it all connects together in one sentence: **_In React, a web app is a structured tree of components that automatically translates state into UI by passing data downward as read-only props and bubbling user interactions back upward via callbacks._**  

## Mental Models

So how can we build these elements from the ground up intuitively and visualize them in order to understand them deeper and not be afraid of seeing them and building with them?  

To start off, a mantra and mental anchor on the data flow: <mark>**_Data flows down, events bubble up_**</mark>

Mathematically we can write the relationship between Components and State as <mark>**_Component + State = UI_**</mark>!

MORE COMING SOON
