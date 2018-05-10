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
* The nested `<li>` elements are selected
* Notice the space between `.main-list` and `li`



