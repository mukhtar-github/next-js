# From JavaScript to React

## Updating the UI with JavaScript and DOM Methods

```html
<!-- index.html -->
<html>
  <body>
    <div id='app'></div>
    <script type="text/javascript">
        // Select the div element with 'app' id
        const app = document.getElementById('app')

        // Create a new H1 element
        const header = document.createElement('h1')

        // Create a new text node for the H1 element
        const headerContent = document.createTextNode(
            'Develop. Preview. Ship. 🚀'
        )

        // Append the text to the H1 element
        header.appendChild(headerContent)

        // Place the H1 element inside the div
        app.appendChild(header)
    </script>
  </body>
</html>
```

## Getting Started with React

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>

    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

    <script type="text/jsx">
      const app = document.getElementById('app')
      ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app)
    </script>
    
  </body>
</html>
```

## Essential JavaScript for React

In the next sections, you will be introduced to some core concepts of React from a JavaScript perspective. Here’s a summary of the JavaScript topics that will be mentioned:

- Functions and Arrow Functions
- Objects
- Arrays and array methods
- Destructuring
- Template literals
- Ternary Operators
- ES Modules and Import / Export Syntax

## React Core Concepts

There are three core concepts of React that you'll need to be familiar with to start building React applications. These are:

- Components
- Props
- State

## Building UI with Components

User interfaces can be broken down into smaller building blocks called components. This modularity allows your code to be more maintainable as it grows because you can easily add, update, and delete components without touching the rest of our application.

The nice thing about React components is that they are just JavaScript. Let's see how you can write a React component, from a JavaScript perspective:

### Creating components

In React, components are functions. A component is a function that returns UI elements. Inside the return statement of the function, you can write JSX. React components should be capitalized to distinguish them from plain HTML and JavaScript, and you use React components the same way you’d use regular HTML tags, with angle brackets <>.

```html
<script type="text/babel">
    const app = document.getElementById('app')

    function Header() {
        return (
            <h1>Develop. Preview. Ship. 🚀</h1>
        )
    }

    ReactDOM.render(<Header />, app)
</script>
```

### Nesting Components

Applications usually include more content than a single component. You can nest React components inside each other like you would regular HTML elements. In your example, create a new component called 'HomePage.' Then nest the 'Header' component inside the new 'HomePage' component.

```html
<script type="text/babel">
    const app = document.getElementById('app')

    function Header() {
        return (
            <h1>Develop. Preview. Ship. 🚀</h1>
        )
    }

    function HomePage() {
        return (
            <div>
                {/* Nesting the Header component */}
                <Header />
            </div>
        )
    }

    ReactDOM.render(<Header />, app)
</script>
```

### Component Trees

You can keep nesting React components this way to form component trees.

![component-tree](https://nextjs.org/static/images/learn/foundations/component-tree.png)

This modular format allows you to reuse components in different places inside your app. In your project, since 'HomePage' is now your top-level component, you can pass it to the ReactDOM.render() method.

```html
<script type="text/babel">
    const app = document.getElementById('app')

    function Header() {
        return (
            <h1>Develop. Preview. Ship. 🚀</h1>
        )
    }

    function HomePage() {
        return (
            <div>
                {/* Nesting the Header component */}
                <Header />
            </div>
        )
    }

    ReactDOM.render(<HomePage />, app)
</script>
```

## Displaying Data with Props

So far, if we were to reuse your 'Header' component, it would display the same content both times.

```javascript
function Header() {
  return <h1>Develop. Preview. Ship. 🚀</h1>
}

function HomePage() {
  return (
    <div>
      <Header />
      <Header />
    </div>
  )
}
```

But what if we want to pass different text or you don't know the information ahead of time because we’re fetching data from an external source? Regular HTML elements have attributes that you can use to pass pieces of information that change the behavior of those elements. For example, changing the *src* attribute of an 'img' element changes the image that is shown. Changing the *href* attribute of an 'anchor' tag changes the destination of the link.

In the same way, you can pass pieces of information as properties to React components. These are called 'props'.
