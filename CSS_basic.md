# CSS Setup and Selectors

## Inline style
```
<p style="color: red; font-size: 20px;">I'm learning to code!</p>
```
* Simply keep adding to the style attribute. 
* Make sure to end the styles with a semicolon (`;`).

## The <style> Tag
```
<head>
  <style>
    p {
      color: red;
      font-size: 20px;
    }
  </style>
</head>
```
* Write the `<style>` tage inside the `<head>`.

## The .css file
* Create a CSS file by using the .css file name extension, like so: style.css

## Linking the CSS File
```
<link href="https://www.codecademy.com/stylesheets/style.css" type="text/css" rel="stylesheet">
```
* Use the `<link>` tag
If in the same direction, use relative path:
```
<link href="./style.css" type="text/css" rel="stylesheet">
```

## CSS selector
### Select by tag name
```
p {

}
```
### Select by class
```
<p class="brand">Sole Shoe Company</p>
```
```
.brand {

}
```

### Select by multiple classes
```
<h1 class="green bold"> ... </h1>
```
```
.green {
  color: green;
}

.bold {
  font-weight: bold;
}
```

### Select by ID name
```
<h1 id="large-title"> ... </h1>
```
```
#large-title {

}
```

## Specificity
* ID > class > tag
* A best practice in CSS is to style elements while using the lowest degree of specificity, so that if an element needs a new style, it is easy to override.
* If it is possible to use tag, use it. Then consider for class and finally ID.

## Chainning selector
```
h1.special {

}
```
* Select only the `h1` elements that have a class of `special`
* Do not have space between `h1` and `.special`

## Nested elements
```
<ul class='main-list'>
  <li> ... </li>
  <li> ... </li>
  <li> ... </li>
</ul>
```
```
.main-list li {

}
```
* All nested `<li>` elements are selected
* Notice the space between `.main-list` and `li`
* There are four different combinators in CSS:
  * descendant selector (space): all children.
  * child selector (>) : immediate children.
  * adjacent sibling selector (+) :  adjacent siblings.
  * general sibling selector (~) : just sblings.


## Important
`!important` can be applied to specific attributes instead of full rules. 
```
p {
  color: blue !important;
}


.main p {
  color: red;
}
```
* The `!important` flag is only useful when an element appears the same way 100% of the time. 
* It's best to avoid !important altogether. 
* If you ever see !important used (or are ever tempted to use it yourself) we strongly recommend reorganizing your CSS. 
* Making your CSS more flexible will typically fix the immediate problem and make your code more maintainable in the long run.

## Multiple Selectors
```
h1, 
.menu {
  font-family: Georgia;
}
```
* Prevent to write repetive code

## Summary for CSS selectors
* CSS can change the look of HTML elements. In order to do this, CSS must select HTML elements, then apply styles to them.
* CSS can select HTML elements by tag, class, or ID.
* Multiple CSS classes can be applied to one HTML element.
* Classes can be reusable, while IDs can only be used once.
* IDs are more specific than classes, and classes are more specific than tags. That means IDs will override any styles from a class, and classes will override any styles from a tag selector.
* Multiple selectors can be chained together to select an element. This raises the specificity, but can be necessary.
* Nested elements can be selected by separating selectors with a space.
* The !important flag will override any style, however it should almost never be used, as it is extremely difficult to override.
* Multiple unrelated selectors can receive the same styles by separating the selector names with commas.


# CSS Visual Rules
## Font Family
* Default value: Times New Roman
* Limit the number of typefaces used on a web page to 2 or 3. It will impact the load speed.
* Use `""` when it contains more than one word.
## Font Size
```
p {
  font-size: 18px;
}
```
## Font Weight
```
p {
  font-weight: bold;
}
```
* Options: `bold`, `normal`
## Text Align
```
h1 {
  text-align: right;
}
```
* Options: `left`, `center`, `right`
## Color
* Foreground color
* Background color
```
h1 {
  color: red;
  background-color: blue;
}
```
## Opacity
```
.overlay {
  opacity: 0.5;
}
```
* 0 (invisible) ~ 1 (fully visible)

## Background Image
```
.main-banner {
  background-image: url("https://www.example.com/image.jpg");
}
```
* Need to use URL


# Some point that I conclude:
* The name of css attribute always use lowercase and `-` to split different words.
* For every CSS block, no need for `;`.
* For every attribute inside CSS block, need `;`.

## Summary for Visual Rules
* CSS declarations are structured into property and value pairs.
* The `font-family` property defines the typeface of an element.
* `font-size` controls the size of text displayed.
* `font-weight` defines how thin or thick text is displayed.
* The `text-align` property places text in the `left`, `right`, or `center` of its parent container.
* Text can have two different color attributes: `color` and `background-color`. `color` defines the color of the text, while `background-color` defines the color behind the text.
* CSS can make an element transparent with the `opacity` property.
* CSS can also set the background of an element to an image with the `background-image` property.
