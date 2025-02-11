# What is a Pure Component and How Will You Implement the Same on Functional Components?

## **1. What is a Pure Component?**

A **Pure Component** in React is a component that renders the same output for the same input (props and state). It automatically implements **shouldComponentUpdate** with a shallow prop and state comparison. This helps in optimizing performance by preventing unnecessary re-renders.

### Why is it important?
Pure Components are useful when you need to avoid re-rendering the component unless there’s a change in the input data. They provide performance benefits for applications that have many re-renders, especially when the component is receiving complex props or data structures.

### **Real-World Example:**
Imagine you have a **UserProfile** component, which displays user data. If the user data hasn’t changed, there’s no need to re-render the entire profile every time something else updates in the app. Using a Pure Component will prevent this unnecessary rendering.

```javascript
class UserProfile extends React.PureComponent {
    render() {
        console.log('Rendering UserProfile');
        return (
            <div>
                <h1>{this.props.name}</h1>
                <p>{this.props.age}</p>
            </div>
        );
    }
}
```

Here, `UserProfile` will only re-render if either `name` or `age` props change.

---

## **2. How to Implement PureComponent in Functional Components?**

In React Functional Components, we don’t have access to `PureComponent`, but we can achieve the same behavior using **React.memo()**.

### **What is React.memo()?**
`React.memo` is a higher-order component that wraps around a functional component and optimizes it by memoizing the result, meaning it only re-renders the component if the props have changed.

### **Implementing Pure Behavior with React.memo:**

```javascript
import React from 'react';

const UserProfile = React.memo(function UserProfile({ name, age }) {
    console.log('Rendering UserProfile');
    return (
        <div>
            <h1>{name}</h1>
            <p>{age}</p>
        </div>
    );
});
```

**How does it work?**

- **React.memo** checks if the props of the component have changed.
- If they haven’t changed, React skips the re-render and uses the previous render.
- If the props have changed, React re-renders the component.

### **Real-World Example:**
Consider a **TaskList** component, where only the list of tasks needs to update, not the user's profile or other unrelated data. By wrapping **TaskList** with **React.memo**, we can prevent unnecessary renders of this component if the tasks haven't changed.

```javascript
const TaskList = React.memo(function TaskList({ tasks }) {
    console.log('Rendering TaskList');
    return (
        <ul>
            {tasks.map((task) => (
                <li key={task.id}>{task.name}</li>
            ))}
        </ul>
    );
});
```

Here, `TaskList` will only re-render if the `tasks` prop changes. If other parts of the app update, but the `tasks` prop remains the same, it won't re-render.

---

## **3. Shallow Comparison**

Both **PureComponent** and **React.memo** perform a **shallow comparison** of the props. This means:
- It checks if the reference of the objects has changed (i.e., if the object is pointing to a different place in memory).
- For primitive types like strings, numbers, and booleans, it checks their values.
  
**Shallow Comparison Example:**

```javascript
const prevProps = { name: 'John', age: 25 };
const nextProps = { name: 'John', age: 25 };

console.log(prevProps === nextProps);  // This will be true because the object references are the same.
```

---

### **4. When Should You Avoid PureComponent or React.memo?**

- If the component is receiving complex objects or arrays that change frequently, `React.memo` might cause more re-renders due to its shallow comparison.
- When performance isn’t an issue, it might not be necessary to use **PureComponent** or **React.memo**.

### **Real-World Example:**
In an app that displays a list of users with names and avatars, wrapping the entire list with `React.memo` could lead to unnecessary renders, as each individual user’s data might change frequently (like online status). Instead, using **React.memo** on individual **UserProfile** components would be more efficient.

---

### **In Summary:**

- **Pure Component**: Optimizes performance by preventing unnecessary re-renders based on shallow prop and state comparison.
- **React.memo**: A way to implement **PureComponent** behavior in functional components by memoizing the component’s render output based on prop changes.

---

**💡 Tip for Interviews**:  
Make sure to emphasize **when to use** these optimization techniques — they should be applied when necessary, especially in larger, more complex React applications where performance may become a concern.

