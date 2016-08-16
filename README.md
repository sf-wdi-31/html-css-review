<!--
Creator: <Name>
Market: SF
-->

![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

# HTML and CSS

### Why is this important?
<!-- framing the "why" in big-picture/real world examples -->
*This workshop is important because:*

HTML is the oldest and most fundamental language of the web.  It contains a page's content, provides structure for that content, and gives the browser important metadata about the page.

CSS lets us style a web page, creating sites that stand out visually. It is an incredibly powerful tool

### What are the objectives?
<!-- specific/measurable goal for students to achieve -->
*After this workshop, developers will be able to:*

- Recognize common HTML tags and attributes.
- Describe the structure of an HTML document.
- Apply CSS styles to HTML elements based on tag, class, or id.
- Distinguish among block, inline, and inline-block elements.
- Draw the CSS box model.

### Where should we be now?
<!-- call out the skills that are prerequisites -->
*Before this workshop, developers should already be able to:*

- Navigate the files in their computer using a command line interface (terminal).
- Create a file with the terminal, modify it with a text editor, and save it.
- Describe the roles of servers, clients, and browsers.
- Explain how HTML, CSS, and JavaScript contribute to a website's front end.

## HTML

### Tags and Attributes

- HTML tags allow you to set up your document's structure and content.

- Attributes allow you to add additional information to a tag.

- "Tags" in HTML code become "elements" in the browser.


<!-- ### Inline and Block Elements

Inline elements -->

### Semantic HTML

Generic page divisions or `div`s are created with the `<div>` tag. They are empty rectangles, and `div` doesn't give any meaningful information beyond that.

Recent versions HTML have introduced more semantic tags with names that mirror their purposes: `header`, `footer`, `nav`, `figure` etc.

![semantic html elements: header, nav, article, section, aside, footer](https://cloud.githubusercontent.com/assets/3254910/12483331/30f9061a-c009-11e5-85e6-43a447431a10.gif)

#### `input`

Inputs allow users to enter data into web forms. (Data is usually  transmitted across the web when the user submits the form.)

Inputs come in different "types" to meaningfully specify what kind of data is being collected.

```html
<input type="text" class="form-control" />
<input type="password" class="form-control" />
```

- [`input` documentation from MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)

##### Anchor:
- Anchor tags are used for linking to other sites, other pages on the current site, or other parts of the current page.

```html
<a href="http://www.google.com">Google Link</a>
<a href="about.html">Link within this Site</a>
```

##### Image:
- Image tags are one way to add images to a site. (CSS background images are another.)

````html
<img src="../public/images/kittens.html" alt="kittens sleeping">
````

### Check For Understanding

1. Sketch out a wireframe for the website from the following image, and label it with semantic HTML elements, class names, or ids.

  ![](https://cloud.githubusercontent.com/assets/3254910/17682332/b2c259dc-62ff-11e6-9fdd-7bd0bb620ba9.png)

2. What are some tags you might include in the head of this page's HTML?

3. Draw the tree structure for the HTML you designed.

4. Bonus: what portions of the web page in the image above might be controlled by JavaScript?


## CSS

CSS provides the look and feel of the website.

### Linking CSS to HTML

There are three different ways to use CSS to style your HTML:

- External style sheet
- Internal Style sheet
- Inline style

#### Inline Styles

To use inline styles, add the style attribute to the relevant tag. The style attribute can contain any CSS property. The example shows us changing the HTML body's background to red:

```html

 <!DOCTYPE>
 <html>
   <head>
     <title>Intro to CSS</title>
   </head>
   <body style="background:red">
   </body>
 </html>
```

<details><summary>Using inline styles is considered poor practice. Why?</summary>
Like most other poor practices, inline styles can lead to unexpected results and bugs.  
* It's easy to miss inline styles when reading through HTML, and most developers expect to see CSS in external stylesheets. Developers may be confused about where a style is coming from.
* Inline styles aren't reusable because they have to be applied to each element individually.
* Inline styles take priority over styles added in other places.
</details>

#### Style Sheets

Style sheets can be written in your HTML (internal) or in a separate CSS file (external).  Whatever style sheet you use, the CSS syntax is the same. We build our CSS with a selector - usually the name of the HTML tag, a specific class of elements, or an element with a unique ID:

```css
selector {
  property_1: value_1;
  property_2: value_2;
}

```

> Note, we can add comments to CSS with `/* your css comment */`. The browser ignores "commented-out" lines.

Do not forget the curly brackets or the semi-colon after the value!


#### Internal Style Sheets

If a _single page_ has a unique style, you can get away with using an internal style sheet - these are defined and written in your HTML using the `<style>` element, inside the head section of an HTML page:

```html

 <!DOCTYPE>
 <html>
   <head>
     <style>
       body {
         background: black;
       }
     </style>
     <title>Intro to CSS</title>
   </head>
 <body>
 </body>
 </html>

```

#### External Style Sheets

With just one file - your external style sheet - you can modify the styles of your entire website.  That's really powerful and helps keep your code organized and separate.

To link the stylesheet to the HTML file, inside the `<head>` tags, we need to add a self-closing `<link>` tag, indicating the type of relations (`rel="stylesheet"`) and the file path.

Developers often have a specific folder for stylesheets, as large applications can have several stylesheets for different parts of the app. We recommend making a `css` folder inside each project to get used to this common file structure.

```html

 <!DOCTYPE>
 <html>
   <head>
     <title>Intro to CSS</title>
   <link rel="stylesheet" href="css/style.css">
   </head>

   <body>
     <p>This is a paragraph element</p>
   </body>

 </html>
```


Our stylesheet file:

```css

body {
  background: red
}

p {
  color: orange;
}

```

### Specificity

One of the most important concepts with CSS is specificity. Imagine you select an element by it's class and give it some style; then, on the next line, you select the same element by it's element name and it's ID - how does the browser know what style to apply?  Well, every element gets a score and it's this score that dictates what CSS property is applied.

[Specificity Calculator](http://specificity.keegan.st/)

Every selector has its place in the specificity hierarchy, and if two selectors apply to the same element, the one with higher specificity wins.  Overall, there are four distinct factors that define the specificity level of a given selector: inline styles, IDs, classes+attributes and elements.  You can calculate CSS specificity with CSS Specificity Calculator:

<img src="https://css-tricks.com/wp-content/csstricks-uploads/specificity-calculationbase.png" style="width: 400px;" />

###Calculating specificity

<img src='https://css-tricks.com/wp-content/csstricks-uploads/cssspecificity-calc-1.png' style="width: 400px;" />

*This is calculated as 0113*

<img src='https://css-tricks.com/wp-content/csstricks-uploads/cssspecificity-calc-2.png' style="width: 400px;" />

*This is calculated as 0023*

<img src='https://css-tricks.com/wp-content/csstricks-uploads/cssspecificity-calc-4.png' style="width: 400px;" />

*This is calculated as 1000*

A couple of rules to think about:

- If two selectors apply to the same element, the one with higher specificity wins
- When selectors have an equal specificity value, the latest rule is the one that counts
- id specificity > class specificity > tag specificity
- Inline styles > internal or external styles
- `!important` defeats all of the above.



#### Box Model


All HTML elements can be considered boxes. Even if you see a circle, it's living within a box.

The CSS box model describes this principal - a box wraps around all HTML elements, and it consists of: margins, borders, padding, and the actual content.  This model allows us to place a border around elements and space elements in relation to other elements.

With CSS properties and values, it is possible to apply specific styles to each of these elements, and change the way they behave and/or display on the page.

The image below illustrates the box model:

![box-model](http://s6.postimg.org/gi8r6c341/css_box_model.png)

_From [www.theslate.org](http://www.theslate.org)_

But what do these different layers mean, and how are they related to one another?


* **Margin** - clears an area around the border; the margin does not have a background color, it is completely transparent

* **Border** - a border that goes around the padding and content; the border is affected by the background color of the box

* **Padding** - clears an area around the content; the space between the content and the border; the padding is affected by the background color of the box

* **Content** - The content of the box, where text and images appear

### Taking Up Space Using `display`

Cool, right? Each HTML element gets its own box to live in.

The box model shows us why, until now, your HTML elements have been sitting on top of one another: by default, they take up the full width of the page.

We can change all this with the first positioning property we'll learn, the `display` property, and the four values we can use with it: inline, block, inline-block, and none.

* An **inline** element has no line break before or after it. This makes the element sit on the same line as another element. It only takes up as much width as it needs (not the whole line). Sometimes we want to take an element that is a block by default and make it behave this way.  (One possible reason is that elements that are inline by default can't contain block elements.) Changing the display of an element to inline doesn't maintain its "box"ness.

* A **block** element has some whitespace above and below it and does not tolerate any HTML elements next to it. This makes the element a block/box. It won't let anything sit next to it on the page and takes up the full width.

* An **inline-block** element is placed as an inline element (on the same line as adjacent content), but it behaves as a block element. This makes the element a block/box with a width and height but will still allow other elements to sit next to it on the same line.

* If you assign **none** as the value of the display, this will make the element and its content disappear from the page entirely!

### Float and Clear

When element sizes are variable or dynamic, we can use `float` to allow text and other elements to wrap around a floated element.  

Consider the html below:

```html

    <div id="container">
        <div id="square1"></div>
        <div id="square2"></div>
        (add 4 paragraphs of lorem ipsum)
        <div id="square3"></div>
        <div id="square4"></div>
    </div>

```


```css
#square2 {
    background-color: blue;
    height: 200px;
    width: 100px;
    float: left;
}
```

The `float: left;` line tells the browser that the "square2" div wants to be as left as possible, so the browser kindly wraps it in a nice text hug.

####  Clear

While floats make other elements aware of their location and get text hugs, clears make other elements aware and are told not to touch.

What would happen if we change the "square2" div's positioning from `float:left` to `clear: right`?

`Clear` is saying "I'm not sure how much space I'm going to take but whatever it is clear off my right side." The text respects its wishes and drops to the line below.

### Check for Understanding

Answer the questions assigned to your group. Feel free to do some research if you're not sure!

**Group 1:**
* What does CSS stand for? How is each word significant?
* What is "semantic" HTML?
* Explain the differences between an element, a class, and an id.

**Group 2:**
* Describe the concept of CSS specificity.
* Where are three *places* you can associate CSS code with an HTML document? Which one is considered a best practice, and why?

**Group 3:**
* Draw the CSS Box Model.
* What values can we use with the `display` property, and what do they do?

**Group 4:**

* What is the difference between `absolute`, `fixed`, `relative` and `static` positioning?
* What does `display: none;` do?

**Group 5:**

* Explain floats and clears.

**Group 6:**

* Why does HMTL have "attributes"? Give a few examples.
* What are the differences between block and inline elements?
* What is inline-block?


## Independent Practice
Practice the skills covered in this workshop with this [training]().

## Closing Thoughts

Semantic HTML is an expectation among modern web developers. Take care to choose semantic HTML elements, class names, and ids. (Semantic naming is also a best practice in JavaScript and across programming languages.)

Masterful CSS requires a lot of memorization (to know what properties can be changed) and experimentation. Don't be afraid to look things up and try things out. You'll build your toolkit over time.  

The most important things to practice right now are:

- using meaningful tags, classes, and ids.
- following best practices to write clean, readable code.
- memorizing syntax for CSS rules, including tag, id, and element selectors.  
- linking external CSS files to HTML and debugging issues with relative and absolute paths.
