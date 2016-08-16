<!--
Creator: <Name>
Market: SF
-->

![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

# HTML and CSS Resource

**Contents**

* [HTML Tags and Attributes](#html-tags-and-attributes)  
* [Semantic HTML](#semantic-html)   
* [Linking CSS to HTML](#linking-css-to-html)  
* [Specificity](#specificity)   
* [Box Model](#box-model)  
* [Display](#display)  
* [Position](#position)  
* [Float and Clear](#float-and-clear)

### HTML Tags and Attributes

HTML tags allow you to set up your document's organization and content.

"Tags" in HTML code become "elements" in the browser.

Attributes allow you to add additional information to a tag.  Some commonly used elements with required attributes are `input`, `a`, and `img`.



#### `input`

Inputs allow users to enter data into web forms. (Data is usually  transmitted across the web when the user submits the form.)

Inputs come in different "types" to meaningfully specify what kind of data is being collected.

```html
<input type="text" class="form-control" />
<input type="password" class="form-control" />
```

- [`input` documentation from MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)

#### anchor
- Anchor tags are used for linking to other sites, other pages on the current site, or other parts of the current page.

```html
<a href="http://www.google.com">Google Link</a>
<a href="about.html">Link within this Site</a>
```

#### image

- Image tags are one way to add images to a site. (CSS background images are another.)
- Always include an alt attribute for accessibility.

````html
<img src="../public/images/kittens.html" alt="kittens sleeping">
````


### Semantic HTML

Generic page divisions or `div`s are created with the `<div>` tag. They are empty rectangles, and `div` doesn't give any meaningful information beyond that.

Recent versions HTML have introduced more semantic tags with names that mirror their purposes: `header`, `footer`, `nav`, `figure` etc.

![semantic html elements: header, nav, article, section, aside, footer](https://cloud.githubusercontent.com/assets/3254910/12483331/30f9061a-c009-11e5-85e6-43a447431a10.gif)




### Linking CSS to HTML

There are three different ways to use CSS to style your HTML:

- External style sheet
- Internal Style sheet
- Inline style

#### Inline Styles

To use inline styles, add the `style` attribute to the relevant tag. The style attribute can contain any CSS property. The example shows us changing the HTML body's background to red:

```html

 <!DOCTYPE>
 <html>
   <head>
     <title>Intro to CSS</title>
   </head>
   <body style="background:red;">
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


The stylesheet file might look like this:

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



### Box Model


All HTML elements are boxes by default. Even if you see a circle, it's living within or made from a box.

The CSS box model describes ways to modify the size and shape of a box, and it consists of: margin, border, padding, and the actual content.  

With CSS properties and values, it is possible to apply specific styles to each of these elements, and change the way they behave and/or display on the page.

The image below illustrates the box model:

![box-model](http://s6.postimg.org/gi8r6c341/css_box_model.png)

_From [www.theslate.org](http://www.theslate.org)_

But what do these different layers mean, and how are they related to one another?

* **Margin** - clears an area around the border; the margin does not have a background color, it is completely transparent

* **Border** - a border that goes around the padding and content; the border is affected by the background color of the box

* **Padding** - clears an area around the content; the space between the content and the border; the padding is affected by the background color of the box

* **Content** - The content of the box, where text and images appear

### Display

The box model shows us why, until now, your HTML elements have been sitting on top of one another: by default, they take up the full width of the page.

We can change all this with the first positioning property we'll learn, the `display` property, and the four values we can use with it: inline, block, inline-block, and none.

* An **inline** element has no line break before or after it. This makes the element sit on the same line as another element. It only takes up as much width as it needs (not the whole line). Sometimes we want to take an element that is a block by default and make it behave this way.  (One possible reason is that elements that are inline by default can't contain block elements.) Changing the display of an element to inline doesn't maintain its "box"ness.

* A **block** element has some whitespace above and below it and does not tolerate any HTML elements next to it. This makes the element a block/box. It won't let anything sit next to it on the page and takes up the full width.

* An **inline-block** element is placed as an inline element (on the same line as adjacent content), but it behaves as a block element. This makes the element a block/box with a width and height but will still allow other elements to sit next to it on the same line.

* If you assign **none** as the value of the display, this will make the element and its content disappear from the page entirely!

### Position

Another CSS property, `position`, can take `relative` or `absolute` values, among others.

#### Static Positioning

HTML elements are positioned static by default. A "static positioned" element is always positioned according to the normal flow of the page and not affected by the `top`, `bottom`, `left`, and `right` properties.

Consider a square:

```css
div#square {
    background-color: gray;
    position: static;
    height: 500px;
    width: 500px;
}
```

This will show underneath the previous element (since `div` is a block element) just as it would without a `position` CSS property.  You rarely explicitly declare `position: static;` like this because it is the default.

#### Fixed Positioning

An element with fixed position is positioned relative to the browser window.  It will not move even if the window is scrolled, so a fixed positioned element will stay right where it is.

Try it out:

```css
div#square2 {
    position: fixed;
    width: 100%;
    height: 100px;
    background-color: blue;
    top: 0;
    left: 0;
}
```


#### Absolute and Relative Positioning

Specifying `position:absolute` _removes the element from the document_ and places it exactly where you tell it to be, in relation to its parent. 

```css
#square1 {
    /* force square to top left corner */
    position:absolute;
    top: 0;
    right: 0;
}
```

Declaring `position:relative` allows you to position the element top, bottom, left, or right relative to where it would normally occur.

```css
#square1 {
    position:relative;
    top: 0;
    left: 40px;
}
```


A page element with "relative positioning" gives you the control to "absolutely position" children elements inside of it. This might not be obvious to everyone - that's probably because this isn't intuitive, at all. Let's look at an example.


![css position relative](https://i.imgur.com/LRd7lBy.png)

The relative positioning on the parent is what matters here. This what would happen if we forgot that:

![](https://i.imgur.com/0vGcPFL.png)

In this small example, it doesn't seem to matter much, but it really is a significant change.

> Without a relative parent, "absolutely positioned" elements are positioning themselves in relation to the body element, instead of their direct parent. So if the browser window grows, that element in the bottom left is going to stick with the browser window.

Using aboslute and relative positioning for layout has fallen out of favor because it's hard to allow flexibility for different screen sizes. 

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

The `float: left;` line tells the browser that the "square2" div wants to be as far left as possible, so the browser kindly wraps it in a nice text hug. 

####  Clear

While floats make other elements aware of their location and get text hugs, clears make other elements aware and are told not to touch.

What would happen if we change the "square2" div's positioning from `float:left` to `clear: right`?

`Clear` is saying "I'm not sure how much space I'm going to take but whatever it is clear off my right side." The text respects its wishes and drops to the line below.
