---
toc: true
layout: post
description: A description of why Svelte is better than React
categories: [markdown, web]
title: Why you should use Svelte instead of React?
---
## State management system
Svelte is a Web Framework which provides an easy to use state management system without the drawbacks of a slow virtual DOM (unlike React and Vue). Additionally, it is very similar to normal HTML/CSS/JS, which means it has less of a learning curve. Svelte uses the .svelte file extension for its files, which are really similar to normal HTML files. If you want to export a javascript variable to your HTML, just export it in a script tag. You can then access it in your HTML by enclosing the variable in curly brackets

```
<script>
export let awesome_var = "Svelte is cool!";
</script>
<h1>{ awesome_var }</h1>
```
When you change the variable, your HTML will automatically be updated. No need for unnecessary calls such as setState in React
```
<script>
export let awesome_var = "Svelte is cool!";
function editVar () {
  awesome_var = "Svelte is really cool!"
}
</script>
<h1>{ awesome_var }</h1>
<button on:click={editVar}>Make Svelte really cool</button>
```

When you press the button, the h1 will automatically update with the new text. In addition, you might have noticed that instead of onclick, I used on:click, which is the way Svelte handles events.

## Slots
Another feature that svelte provides is slots, which makes it super easy to use and create custom components. Essentially, I can template my component, and then have the consumer of the component fill in the HTML for some of the parts. For instance, let’s say I'm creating a layout component, which has 3 divs. We can then create slots, which would allow the user of the component to specify what to put in those divs. This is what I would put in CustomComponent.svelte.

```
<!-- These divs could be styled by the component creator -->
<div>
  <slot name="div1">
</div>
<div>
  <slot name="div2">
</div>
<div>
  <slot name="div3">
</div>
```
Now, in my app component, I can use this CustomComponent I created by importing it. I can then easily specify what to put in the slots.
```
<script>
//import CustomComponent
import CustomComponent from "./CustomComponent.svelte"
</script>
<CustomComponent>
  <span slot="div1">This is the text I want in div1</span>
  <span slot="div2">This is the text I want in div2</span>
  <span slot="div3">This is the text I want in div3</span>
</CustomComponent>
```

# CSS
Additionally, CSS is exactly the same as you would do with a normal HTML file, you would just add a style tag. For instance, here I make all the spans have a background color of red.
```
<style>
span {
  background-color: red;
}
</style>
```
One thing to note about styles with svelte is that they are shallow. This means if I had some spans in my CustomComponent, the styles I specify in my App component would not apply to those spans.

Overall, with all these features, it is clear that you should use Svelte as your go-to web framework.