# Learning Vue

## Initial the Vue project
```
npm install -g vue-cli //install vue-cli gloablly
vue init webpack myapp //create new project with webpack template, may have some error for the miss of node package
cd myapp
npm install //install dependencies
npm run dev  //run dev server
npm run build //build application to production
```

## Declarative rendering
### HTML file
```
<div id="app">
  {{ message }}
</div>
```
### JS file
```
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```
"el" stand for element, it is related with the id="app" in html file.

## Directive
start with "v-", they are special attributes provided by Vue, they apply special reative behavior to rendered DOM.
```
<element v-directiveId="[argument:] expression [|filters...]">
</element>
```
Simple directive examples
```
<span>{{ msg }}</span>   //basic interpolation
<span v-text="msg"></span>   //using the v-text directive
<span v-html="msg"></span>   //parses HTML
<span v-once>{{ msg }}</span>   //one-time interpolation
```

## Conditionals and loops
### HTML
```
<div id="app-3">
  <span v-if="seen">Now you see me</span>
  <li v-for="user in users">{{ users.name }}</li>
</div>
```
### JS
```
var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
    users:[
        {name: 'Bob'}
        {name: 'Kathy'}
    ]
  }
})
```

## Class & style binding
```
<div v-bind:class="{active: isActive}"></div>
<div v-bind:class="{color:activeColor}"></div>
```
```
data: {
    isActive: true,
    activeColor: 'red'
}
```

## Components
* Provide organization & encapsulation
* Re-usable code
* Can be separated into vue files
```
//register
Vue.component('my-component', {Template: 'This is my component'})
```
```
<div id="app">
    <my-component></my-component>
</div>
```

## Additional tools & plugins
* vue-router - official router deeply integrated with Vue.js core
* vue-resource - handle web requests
* vue-async-data - async data loading
* vue-validator - form validation plugin
* vue-devtools - chrome devtools extention
* vue-touch - touch gestures using Hammer.js