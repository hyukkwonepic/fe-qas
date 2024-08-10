---
title: Thnking in React
---

# [Thnking in React](https://react.dev/learn/thinking-in-react)

https://react.dev/learn/thinking-in-react



### What are the five steps to implement a UI in React?

The five steps are:
1. Break the UI into a component hierarchy
2. Build a static version in React
3. Find the minimal but complete representation of UI state
4. Identify where your state should live
5. Add inverse data flow

### What is the first step in breaking the UI into a component hierarchy?

Start by drawing boxes around every component and subcomponent in the mockup and naming them.

### What principle can be used to decide if you should create a new component?

The single responsibility principle, which states that a component should ideally only do one thing.

### What is the recommended approach when building a static version of your app?

Build a version that renders the UI from your data model without adding any interactivity at first.

### What is the primary way of passing data from parent to child components in React?

Props are used to pass data from parent to child components.

### What is meant by "one-way data flow" in React?

Data flows down from the top-level component to the ones at the bottom of the tree.

### What is the key principle for structuring state in React?

Keep it DRY (Don't Repeat Yourself) - figure out the absolute minimal representation of the state your application needs.

### How can you identify if a piece of data is state?

Ask these questions:
- Does it remain unchanged over time? If so, it isn't state.
- Is it passed in from a parent via props? If so, it isn't state.
- Can you compute it based on existing state or props in your component? If so, it isn't state.

### Where should state be placed in a React application?

State should be placed in:
- The common parent component of components that need it
- A component above the common parent
- A new component created solely for holding the state

### What is the purpose of the useState() Hook in React?

useState() is used to add state to a component.

### What is meant by "inverse data flow" in React?

It refers to the process of passing callbacks from parent components to child components to allow children to update the state in parent components.

### Why is it important to make data flow explicit in React?

Making data flow explicit helps in understanding how the application works and makes it easier to find and fix bugs.