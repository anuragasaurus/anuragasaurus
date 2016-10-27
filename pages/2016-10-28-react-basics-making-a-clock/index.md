---
title: React Basics - making a clock
date: "2016-10-28T22:40:32.169Z"
layout: post
readNext: "/hello-world/"
path: "/react-basics-making-a-clock/"
---

Hello guys, this is a post on react basics. This is a very basic tutorial written for people who are beginner in React.

So, below is what we will be making.

<p data-height="265" data-theme-id="0" data-slug-hash="GjagqV" data-default-tab="js,result" data-user="anuragasaurus" data-embed-version="2" class="codepen">See the Pen <a href="https://codepen.io/anuragasaurus/pen/GjagqV/">React Clock CodePen</a> by anuragasaurus (<a href="http://codepen.io/anuragasaurus">@anuragasaurus</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>


So, I'll explain to you what's happening.

In react, we make webapps by making components. For example, we need to make a clock here so we will make a component for it. We make one component which wraps all the components and insert it the HTML with this code,

```javascript
render(
  <App />, document.getElementById("app")
);
```

Above we are inserting App component in a HTML element whose id is "app". We can devide this App component into multiple small components which are easier to work with. As we have only one small clock component, we will only be working with one component.

In above code we are writing in javascript es6 syntax. Every Component should have a render function which should return a jsx element. React has some lifecycle methods like componentDidMount, componentWillUnmount. componentDidMount runs when component is first rendered on page, componentWillUnmount runs when it is unmounted from page.
Every component has a state. State is a object in which we store data which we might need. We define initial state in constructor function. To change the state we call setState method. If state of a component is changed react automatically rerenders the component.

For our clock app we call setInterval function which will call setState method every second to change the state. As the state will change the component will rerender. This setInterval function is placed inside componentDidMount so it runs as soon as the component is mounted on webpage. Hope that makes sense. Other than that getTimeString is a helper function which converts the timestamp returned by Date.now() function to readable string.
