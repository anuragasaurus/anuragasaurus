---
title: React Basics - making a markdown parser
date: "2016-11-07T22:40:32.169Z"
layout: post
readNext: "/react-basics-making-a-clock/"
path: "/react-basics-making-markdown-parser/"
---

Hello guys, this is a post on react basics. This is a very basic tutorial written for people who are beginner in React.

If you haven't read [making a clock with React](http://anuragasaurus.com/react-basics-making-a-clock/), you should read it first, because it covers basic concepts of React.

So, below is what we will be making. (If the codepen embed doesn't load, try refreshing the page.)


<p data-height="265" data-theme-id="0" data-slug-hash="WGBgxQ" data-default-tab="js,result" data-user="anuragasaurus" data-embed-version="2" data-pen-title="React markdown parser" class="codepen">See the Pen <a href="https://codepen.io/anuragasaurus/pen/WGBgxQ/">React markdown parser</a> by anuragasaurus (<a href="http://codepen.io/anuragasaurus">@anuragasaurus</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

I have created a component named "TextArea" which is the main and only component. It's state consits of `inputValue` and `parsedValue` of markdown input.

```javascript
this.state={
	inputValue:"# hello, write some `markdown` here",
	parsedValue:""
}
```
TextArea renders a input element where we will write in markdown and a div which will display the result. `handleChange` function keeps the state of component and value in input field in sync.

```javascript
handleChange(e) {
    this.setState({
      inputValue: e.target.value,
      parsedValue: marked(e.target.value)
    });
}
```

I am using a mardown parsing library [marked](https://github.com/chjj/marked). As input value changes, I pass the input value in marked function which is exposed by "marked" and store it in the `this.state.parsedValue`.

`componentDidMount` is a react lifecycle function which is run after component is mounted on screen.

### Edit:

I searched for alternative for `dangerouslySetInnerHTML` but couldn't find one. They named it `dangerouslySetInnerHTML` to make developer aware of the risk of XSS attack when they use it. To avoid the risk of XSS attack, we can use `DOMPurify` which sanitizes the html.