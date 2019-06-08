# Vue.js Basics

## **Slots and V-Slot Directive**

### **SLOTS**

`Slots` in Vue.js are an incredibly powerful concept. I like to think of `slots` almost as **super charged props**. Props allow us to pass data (state) from parent to child components, whereas `slots` allow for us to pass down entire elements, blocks, and other components to be used in conjunction with the child component.

Slots are what are known as _content distribution_ elements. We register a `<slot></slot>` element somewhere in a child components template block, and that `<slot>` tag essentially acts as a content placeholder. Which may sound confusing at first, but they are actually very simple and once we see how to use `slots` it will all make sense.

Lets look at a basic example where we are passing in a `<p>` element from the parent to in between the component tags. Vue then plugs that content into the `slot` element.

```html
<template>
  <div>
    <h2>Vue.js Slots | Parent Component
    <child-component>
      <!-- we can add html and content here -->
        <p>Content text will go here!</p>
      <!-- such as the above -->
    </child-component>
  <
```

```html
<template>
  <div>
    <h2>Vue.js Slots | Child Component</h2>
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>
```

Which will in-turn render out to the follow markup.

```html
<template>
  <div>
    <h2>Vue.js Slots | Child Component</h2>
    <div class="content">
      <p> Content text will go here! </p>
    </div>
  </div>
</template>
```

A couple a things to keep in mind about slots..

- component must be opening / closing tag syntax, not self-closing syntax.
- the `<slot>` tag acts as a `<template>` tag in that it doesn't get rendered
- the `slot` / `slot-scope` api has been depricated in favor of the unified `v-slot` syntax

Using `slots` help us to increase reusability and cut down on code quite drastically. Instead of having an entire stateful Vue Component being used, we can essentially eliminate everything but the root `template` and the inner `slot` tag.

Vue likes us to keep track of our slots efficiently and we do so by making use of the **named slot** syntax at the child component level in conjunction with the new `v-slot` syntax at the parent component level. Doing so allows us to use multiple slot instances in the same component block.
