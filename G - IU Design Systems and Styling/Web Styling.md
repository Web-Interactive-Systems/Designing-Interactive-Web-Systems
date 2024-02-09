---
type: NoteCard
tags: []
---

# Web Styling

Web styling is one of the important ways to create unique experiences, engaging interfaces, and responsive web designs.

![{width=273,height=auto}](../attachments/webdev101-css.png)Illustration by [Tomomi Imura](https://twitter.com/girlie_mac)

CSS, or Cascading Style Sheets, solves important problems for the web, among other things:

- Unique user experiences: Make web apps look and feel beautiful and appealing
- Engaging interactions: Allows sophisticated styling and interactions like transitions, animations, and transformations
- Responsive web design (RWD): Make apps look and feel nice on different screen sizes

::::cal
CSS is an evolving language, and many CSS APIs are not supported by browsers. In case of doubt, you can check using <https://caniuse.com/>

::::

::::cal
Remember that all browsers come with a set of default styles for most DOM elements. Default styles that come with browsers are not consistent with each other. This means the default style of a button will look different on Chrome compared to Firefox compared to Edge. There are tools like [normalize](https://github.com/necolas/normalize.css) that allow us to reset browsers’ default styles.

::::

Modern web frameworks provide two main ways to style web apps:

1.  Inline styles: Styles defined with `style` prop
2.  CSS classes: CSS classes  `className` or `class` prop, depending on the framework

CSS classes need to be defined. This can be:

1.  Global external styles: Styles defined in CSS files
2.  Internal styles: Styles defined in single file components (SFC) using `<style>` tag (e.g., Vue, Svelte) or other internal styles libraries.

### **The inline `style` prop:**

- Using HTML, we pass a string of CSS (the normal way of writing CSS kebab-case):

<!---->

    <div style="margin-top: 20px; background-color: blue;"></div>

- Using React, we pass an object of CSS (The CSS-in-JS way of writing CSS camel-case):

<!---->

    <div style={{marginTop: 20, backgroundColor: 'blue'}}></div>

In React, the `{{` and `}}` syntax is a combination of a JSX expression and a JS object expression. The same example above could be written like so:

    // object
    const myStyles = {marginTop: 20, backgroundColor: 'blue'}

    // style
    <div style={myStyles} ></div>

In React we use `camelCased` rather than `kebab-cased` for CSS property names.

Often in modern frameworks, we bind (link) CSS properties to state objects this way, when the state changes the UI changes.

Here is an example using VueJS and inline style.

    // a way to create state variables in VuJS
    const styleObject = reactive({
      color: 'red',
      fontSize: '13px'
    })

    <div :style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>

Notice \`: style\` is a way to bind state variables to a DOM template.

In Vue we can use both `camelCased` and `kebab-cased` for CSS property names.

Svelte also provides a similar API,

    <div style="background-image: url('{bgImage}'); color:{color};">Work!</div>

Style directives are also provided by Svelte: `style:css_property={value}`

    <div
      style:position="absolute"
      style:top={position === 'absolute' ? '20px' : null}
      style:pointer-events={pointerEvents ? null : 'none'}
    ></div>

### **The inline `class or classname` prop:**

In HTML, we can apply a class name to a DOM element with the `class` attribute.

In JSX (React), you use the `className` prop.

In Vue we have two options, `class `for static css class or \`: class\` with data binding

```

<div
  class="static"
  :class="{ active: isActive, 'text-danger': hasError }"
></div>
```

Svelte propose class directive option: \`class

\={value}\` or \`class

\` for short when the name and value match.

    <!-- These are equivalent -->
    <div class={isActive ? 'active' : ''}>...</div>
    <div class:active={isActive}>...</div>
