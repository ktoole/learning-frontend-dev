# Learning CSS

## General Notes

The point of CSS is to separate our presentation from our document structure. 
You can test with a style tag in the top of the html file after the head tag.  It's best to only
do this for quick css testing.  
Best practice is to create a separate CSS file for your css

You could also do this using the inline style like so:
```
<div style="background-color:  orange;">Welcome to CSS course!</div>

```

Add link tags to css files in the header section of your page
```
<link rel="stylesheet" type="text/css" href="styles.css">
```
- The rel attribute identifies the relation between the current document and the linked document.
- The type attribute specifies the media type.
- The href attribute provides the location of the document.

We use selectors to target the HTML elements we want to style with CSS. We do this by associating declarations to elements on the web page.

The four basic selectors are:

- Element
- Class
- ID
- Universal

For example, the following css will...
```
p {
  color: #14288A;
  font-size: 24px;
}
```
...target all p tags on our web page. So, if we have multiple paragraphs, they all change to red.

Class and Ids

- Every HTML element has two attributes that we commonly use when associating our styling to a specific element: the class and the id attributes. They’re used similarly, however, there’s a fundamental difference between the two. In an HTML document, the same class value can be repeated across multiple elements, but an id value can only be used once. In other words, we use classes when we need to select an element with two or more specific class names.

In our CSS, we’ll prefix with a period (.) to denote a class, and for an id, we’ll use the hash (#) symbol. For example...
```
#content {
    background-color: #E9F3F8;
    padding: 20px
}

.text {
    color: #14288A;
    font-weight: bold;
}
```

It’s worth noting that ID selectors can’t be reused. Strictly speaking, we should always try to use a tag name, a semantic HTML5 element, or even a pseudo-class before we decide to use an ID.

Universal Selector
The asterisk (*) selects all elements. The following example sets the background-color of all elements on the web page:

```
* {
    background-color: yellow;
}
```

This isn't recommended however.

Connecting a number of selectors thru commas like so
```
p, .city {
  color: #14288A;
}
```

Span Tag
In HTML, the span tag is a generic inline container element. Span tags usually wrap sections of text for styling purposes or for adding attributes to a section of text without creating a new line of content.

To select a nested element within a tag, add a space between the two tags like so. The following code modifies the style
for the span tag within the p tag:
```
p span {
  color: #002AFF;
}
```

Suppose we want to make sure that it only selects the element at the first nesting level. We can use the > symbol, as shown in the code below:
```
p > span {
  color: #002AFF;
}
```

We can also select an adjacent sibling, which is an element that has a specific element precede it. We do so using the plus sign (+) as follows:

```
p + span {
  color: #002AFF;
}
```

We can also use the tilde symbol (~) when working with sibling selections. We use this as a general sibling selector that selects all preceding elements, not just the first, as the plus operator (+) does:
```
p ~ span {
  color: #002AFF;
}
```

## Attribute Selectors

There are multiple types: presence and value selectors and substring matching selectors

## Pseudo-classes
- Pseudo-class selectors are predefined keywords that define the state of an element or target a child element. They occur pretty frequently, and we can see them in action when a colon follows an element. An example of this is the :hover selector:
```
a:hover {   
   /* Hover is a pseudo-class! */ 
}
```

Most common pseudo-class selectors
- state
- validation
- structural
- relational

### State Pseudo-class selectors

The :link selector represents a link that hasn’t been visited yet.
  - Styles defined by the :link pseudo-class selector are overridden by any subsequent state pseudo-class selector (:active, :hover, or :visited). So, it’s always best to put the :link rule before the rest.

The :visited selector selects all links that have been visited in the current browser session. The example below applies to all "a" tags
```
a:visited {
    color: red;
}
```

The :hover selector is used whenever the user’s cursor hovers over a link without clicking it.
```
a:hover {
    color: orange;
    cursor: pointer;
}
```

The :active selector selects a link when it’s being activated. This could be when it’s clicked, tapped (on a touchscreen), or even when tabbed to (as in a navigation item) on a keyboard.
```
a:active {
    color: pink;
}
```

### Validation Psuedo-class selectors
The :focus selector selects an element that has focus from the user’s selection. These could be links, for example:
```
a:focus {
    color: green;
}
```

It can also be for form inputs or textarea, as shown in the code below:
```
input:focus {
    background: yellow;
}
textarea:focus {
    background: pink;
}
```

The :target selector is used to select an id. There will be a match if the hashtag in the current URL matches that particular id. It’s used for inner navigation, so if you’re located at www.example.com/#projects, the selector #projects:target will match. We can use this to build tabs on a page, and the tabs can link to our hashtags that activate when the panels match our :target selectors.

The :enabled selector is the default pseudo-class. It selects all enabled inputs. Every form element is enabled by default, unless we add the :disabled selector.

The :disabled selector selects a form element with the disabled state. Our element can’t be selected, checked, activated, or given focus in this state.

The :checked selector selects checkboxes & radio buttons that’ve been checked or selected.

The :required selector selects input elements that contain a required attribute. For example:
```
<input type="email" required>
```

### Structural Psuedo-class selector
Structural pseudo-class selectors select additional information from the DOM, which can’t be targeted otherwise.

The :root selector selects the highest element in a document. This is almost guaranteed to be the <html> element, unless we’re using a different markup language, such as SVG or XML.
```
:root {
    background-color: coral;
}
```

The :first-child selector selects the first element within its parent element.

The :last-child selector selects the last element within its parent element.

The :nth-child() selector uses a simple formula to select elements depending on their order.
  - All :nth pseudo-classes take an argument via a formula. The formula may be a single integer or structured as an+b, or it could use the keywords odd or even.

In the an+b formula:

- The a is a number.
- The n is a literal number and will represent a value assigned to the variable n.
- The + is an operator (it may also be set to the minus sign (-)).
- The b is an optional number (it’s only required if an operator is being used).

Note: 2nn designates any items whose position is a multiple of 2, while 5 is the offset from where it should start.

The :nth-of-type() selector is similar to the :nth-child. However, it’s used in places where different elements are at the same level. The selector matches each element of the nth-child of a particular type.

The :nth-last-of-type() selector is similar to :nth-of-type, only it counts in reverse (from the bottom up).

The :nth-last-child() selector is similar to :nth-child, but it also counts in reverse.

The :only-of-type selector selects an the element only if it’s one-of-a-kind (within its parent).

The :not() selector accepts an argument inside the parentheses (which can be any selector). It selects all elements within the parent that aren’t represented by the argument. Example Use:
```
li:not(.first-item) {
    color: red;
}
```

## Pseudo-elements
A pseudo-element styles specific parts of an element. For example, we could use it to style the first letter (::first-letter) or line (::first-line) of a given element. Alternatively, we could use it to add content before (::before) or after (::after) an element.
Example:
```
p::first-letter {
  color: red;
  text-transform: uppercase;
}
```
In the example above, every <p> first letter is selected using the ::first-letter pseudo-element. The color is set to red and the text is set to uppercase.

We can identify a pseudo-element when they begin with a double colon (::). A single colon can also be used, but the standard convention is to use a double colon to clarify that these are different from pseudo-classes.

Some common pseudo-elements include the following:

-   The ::first-letter pseudo-element is used to style the first letter of a text.
-   The ::first-line pseudo-element is used to style the first line of a text.
-   The ::before pseudo-element lets us add rules before an element.
-  The ::after pseudo-element lets us add rules after an element.
-   The ::selection pseudo-element selects text targeted by the user.



Note: The ::first-letter can only be applied to block-level elements. A block-level element is any element that starts on a new line, such as <div>, <h1> to <h6>, <p>, and so on. It can’t be applied to inline elements such as or <code>.

A neat trick is to combine pseudo-element selectors with classes:

```
p.summary::first-letter {
  color: red;
}
```
Here, we can set the style for the first letter of every paragraph with the summary class.

### The ::before and ::after pseudo-elements
```
div::before {   
   content: "before"; 
} 
div::after {   
   content: "after"; 
}
```
Note: The content property is required, because it specifies the content to be added.

The ::before pseudo-element can be used to insert new content before the content of an existing element.

A common use case would be if we wanted to add an icon before the content of an <h1> element:

```
h1::before {
  content: url(icon.png);
}
```

We can use the content property to insert whatever content we like:

```
p::before {
  content: "Check this out: ");
  color: green;
  font-weight: bold;
}
.company::before {
   content: url("images/logo.png");
}
```

The ::selection pseudo-element is another extremely useful property. It selects the portion of an element that the user highlights.


## CSS Core Concepts

Inheritance
- When working with fonts, we don’t have to apply our font-family or font-size styles to every element on our page. We can set these styles on the body tag and every child will inherit it.
Inheritance helps us write our CSS much more concisely by reducing repetition. As a result, we don’t have to explicitly set each property in every child element.

Enforcing a property

If a property isn’t inheritable by default, we can force its children to inherit properties. In the child selector, set the property to inherit.

For example:
```
body {
   background-color: red;
}
p {
   background-color: inherit;
}
```

Our web page, <body> is given a red background-color. Typically, other elements won’t inherit background properties. We use background-color: inherit to enforce this on a <p> element.

There are only certain properties that are inheritable

Avoiding property

The reverse is also possible. By using the revert keyword, the property won’t be inherited from its parent. In this case, the value is reverted to its parent element.

For example:
```
body {
   background-color: red;
}
p {
   background-color: revert;
}
```

## Specificity
When multiple CSS rules target an element — specificity comes into play!
The more specific rule will always win. And if two or more rules have the same specificity, the one that appears last wins.
We have an element that is both an ID & class selector target. In this case, the ID selector has a higher specificity. Meaning the style of the ID selector will apply instead of any style set by the class selector.

For example, say you want all your button elements to have a blue color. You could use a class selector to define all elements under the button class to have a blue background color (hex color code #14288A) and a white font color (#FFFFFF). But you want to have a subscribe button to be an exception to this rule (so it stands out!). Then you could use an ID selector to define the specific button with the ID (e.g., "homepage”) to have an orange background color (#F59100) and a black font color (#000000). All other button elements that don’t have the ID “homepage” will still follow the CSS rule of the class selector.  Example HTML and CSS below:

HTML:
```
<html>
 <head>
 </head>
 <body>
   <button type="button" class="btn" id="homepage">Subscribe</button>
   <button type="button" class="btn">Subscribe</button> </body>
</html>
```
CSS:
```
#homepage {
  background-color: #F59100;
  color: #000000;
}

.btn {
  background-color: #14288A;
  color: #FFFFFF;
}
```

Understanding how specificity works will greatly reduce any frustrations we may have with CSS.

If we’ve applied a style to an element that isn’t taking effect, the culprit is likely to be a selector that isn’t specific enough!

## How to calculate specificity?
To perform the calculation, think of 4 slots with each of them starting at 0.

0 0 0 0

The slot on the left is the most important, and the rightmost is the least important.

Therefore 1 0 0 0 is higher than 0 1 0 0.
Slot 1

The first slot, the rightmost one (0 0 0 0), is the least important.

This value changes when we have a type selector. A type is a tag name. If you have more than one type selector in the rule, increment the value stored in this slot.

For example:
```
p {}         /* 0 0 0 1 */
span {}      /* 0 0 0 1 */
p span {}    /* 0 0 0 2 */
p > span {}      /* 0 0 0 2 */
div p > span {}  /* 0 0 0 3 */
```
Slot 2

The number in the second slot is determined by the following:

    Class selectors
    Pseudo-class selectors
    Attribute selectors

Every time a rule contains one of the above selectors, we increment the value of the second column from the right.

For example:
```
.city {}        /* 0 0 1 0 */
.users .city {}     /* 0 0 2 0 */
[type="button"] {}  /* 0 0 1 0 */
:hover {}       /* 0 0 1 0 */
```
And naturally, slot 2 selectors can be combined with slot 1 selectors:
```
p .city {}           /* 0 0 1 1 */
input[type="button"] {}  /* 0 0 1 1 */
.images img:hover {}     /* 0 0 2 1 */
```
Slot 3

Slot 3 is reserved for id’s.

Every HTML element can have an id attribute assigned. And we can use id’s in our stylesheet to target elements specifically.

For example:
```
#city {}    /* 0 1 0 0 */
.user #city {}  /* 0 1 1 0 */
#city span {}   /* 0 1 0 1 */
```
Slot 4

Slot 4 is altered by inline styles. Any inline style will have precedence over any rule defined in an external CSS file or inside the style tag in the page header.

For example:
```
<p style="color: yellow">Text</p>  /* 1 0 0 0 */
```
Even if any other rule in the CSS defines the color, the inline style rule will be applied.

There is just one exception— if !important is used.

This rule will take precedence over any rule with more specificity.

Adding !important to a CSS rule will be more important than any other rule.

The best practice is not to use importance. Instead, you should look for a more specific selector.

## CSS Units
- Pixels and Percentages
  - Percentages let us specify values as a percentage, relative to the same property in the element’s parent. Example below:
```
.parent {
  width: 600px;
}

.child {
  width: 50%;  /* 300px */
}
```

- Fonts and Relative Units
  - em units
    - The em unit is the value assigned to the element’s font-size, and its exact value changes between elements. The measurement itself is the width of the letter “m.”
    The length changes only if we change the font-size. It doesn’t change if the font-family is adjusted. By default, 1em is equal to 16px.
    If any CSS changes the font size, 1em becomes the equivalent of whatever the new font-size is.
    To return to our example, 30em means 30 times the current font size.
  - rem units
    - The rem unit is similar to em, only instead of changing based on the font size of the current element, it changes based on the root (:root {}) element font size.
  - ex units
    - The ex unit is similar to em. However, it’s based on the height of the letter “x.”
    - Unlike em units, this value can change depending on the font-family used & the font-size.
  - ch units
    - The ch unit is like the ex unit, except instead of measuring the height of “x,” it measures the width of the number zero.
    - It also changes as the font-family changes.

- Viewport Units
  - The viewport width (vw) unit represents a percentage of the user’s viewport width:

```
.element {
  width: 20vw;
}
```
It’s similar to percentage, but the value remains consistent regardless of the value held by the parent elements. This is similar to how rem units remain relative to the root.
These vw units are often used for sizing responsive types, which is the type that adjusts its size based on the user’s screen size.

The viewport height unit represents a percentage of the user’s viewport height. So, 20vh equals 20% of the height of the viewport

The viewport minimum (vmin) unit is the minimum value between the height or width as a percentage.

The viewport maximum (vmax) unit is the maximum value between the height or width, and it’s given as a percentage.






## Links/Resources