# React HOC and Animations

## Learning Competencies
By the end of this topic you will be learning about 

- What are Higher order components(HOC) and why do we use them
- How to extend the pre-defined Component using HOC
- How to build your own HOC in your application
- Animations in React
- Animate elements using React
- different Animation Add-ons in React

## Overview

## Higher Order Components

Higher order components are JavaScript functions which are used for adding additional functionality to existing component. These functions are pure which means they are receiving data and returning values according to that data. If data changes, higher order functions is re-run again with different data input. If we want to update our returning component, we don't have to change our HOC. All we need to do is change the data that our function is using.

Higher order component (HOC) is wrapping around "normal" component and provide additional data input. It is actually a function that takes one component and returns another component that wraps the original one.

React official doc says 

> A higher-order component (HOC) is an advanced technique in React for reusing component logic. HOCs are not part of the React API, per se. They are a pattern that emerges from React’s compositional nature.
> 
> Concretely, a higher-order component is a function that takes a component and returns a new component.

```js 
const EnhancedComponent = higherOrderComponent(WrappedComponent); 
```

We will use simple example, so you can easily understand Higher order components concept works. The `MyHOC` is a higher order function that is used only to pass data to MyComponent. This function takes MyComponent, enhances it with newData and returns the enhanced component that will be rendered on screen.

```js
import React from 'react';

var newData = {
   data: 'Data from HOC...',
}

var MyHOC = ComposedComponent ⇒ class extends React.Component {

   componentDidMount() {
      this.setState({
         data: newData.data
      });
   }

   render() {
      return <div><ComposedComponent {...this.props} {...this.state} /></div>;
   }
};

class MyComponent extends React.Component {
   render() {
      return (
         <div>
            <h1>{this.props.data}</h1>
         </div>
      )
   }
}

export default MyHOC(MyComponent);
```

If we run the app, we will see that data is passed to MyComponent and *`Data from HOC`* is printed in the browser.

**NOTE**: Higher order components can be used for different functionalities. These pure functions are the essence of functional programming. Once you are used to it, you will notice how your app is becoming easier to maintain or to upgrade.

## Animation in React

### Add-ons
The `ReactTransitionGroup` add-on component is a low-level API for animation, and `ReactCSSTransitionGroup` is an add-on component for easily implementing basic CSS animations and transitions.

**ReactCSSTransitionGroup**: `ReactCSSTransitionGroup` is a high-level API based on `ReactTransitionGroup` and is an easy way to perform CSS transitions and animations when a React component enters or leaves the DOM. It’s inspired by the excellent [ng-animate](https://docs.angularjs.org/api/ngAnimate) library.

Setting up Animation

Let's start by trying out a simple animation in React. Install the `react-addons-css-transition-group` to the project.
```
npm install react-addons-css-transition-group
```

Import ReactCSSTransitionGroup inside the app.js file.
```js
import ReactCSSTransitionGroup from 'react-addons-css-transition-group'
```

Create a `Home` component, wrap up the `h2` tag inside the `ReactCSSTransitionGroup` tag
```html
<div>
    <ReactCSSTransitionGroup transitionName="anim" transitionAppear={true} transitionAppearTimeout={5000} transitionEnter={false} transitionLeave={false}>
        <h2>Hello world..!</h2>
    </ReactCSSTransitionGroup>
</div>
```
Using the ReactCSSTransitionGroup tag, you have defined the portion where animation would take place. You have specified a name for the transition using transitionName. You have also defined whether the transition appear, enter and leave should happen or not.

Using the transition name defined inside the ReactCSSTransitionGroup, you'll define the CSS classes which would be executed on appear and when in active state. Add the following CSS style to the index.html page.
```css
.anim-appear {
  opacity: 0.01;
}
 
.anim-appear.anim-appear-active{
  opacity: 2;
  transition: opacity 5s ease-in;
}
```

As you would have noticed, you need to specify the animation duration both in the render method and in the CSS. It's because that's how React knows when to remove the animation classes from the element and when to remove the element from the DOM.

Save the above changes and refresh the page. Once the page has loaded, within a few seconds you should be able to see the animated text.

## Exploration

- [HOC for beginners](https://hackernoon.com/higher-order-components-hocs-for-beginners-25cdcf1f1713)
- HOC in react official [doc](https://reactjs.org/docs/higher-order-components.html)
- Recommended [video](https://www.youtube.com/watch?v=Yfr-gUAfyw8) for HOC
- [React animation](https://dev.to/underdogio/adding-animations-to-your-react-app-with-react-transition-group)
- React animation official [doc](https://reactjs.org/docs/animation.html)
