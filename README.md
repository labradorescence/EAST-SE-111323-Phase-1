# Lecture # 3 - DOM Manipulation
## SWBAT
- [ ] Explain what the DOM is
- [ ] Traverse the DOM tree
- [ ] Select single DOM elements with `.querySelector()` and `.getElementById()`
- [ ] Select multiple elements with `.querySelectorAll()` and `.getElementsByClassName()`
- [ ] Add text content to an element with `.textContent`
- [ ] Create elements with `document.createElement()`
- [ ] Append elements to the DOM with `.appendChild()` and `.append()`
- [ ] Remove content with `.remove()`
- [ ] Explain the dangers of `.innerHTML` and when it's safe to use


## Document Object Model
The DOM is an interface for web documents. A tree of Node objects that represent a web page. These Nodes allow access and change to the Document. 

## Selecting DOM elements
To manipulate the DOM, we need to use methods to traverse it and find the elements we are looking for. 


```
// Single elements
// document.querySelector() will traverse the DOM and return the first element of the matching tag, class, or id passed as an argument
// 'tag' looks for the first matching tag
document.querySelector('div')

// '.class' will look for the first matching class
document.querySelector('.someClass')

// '#id' will look for the first matching id
document.querySelector('#someID')

// document.getElementById() traverse the DOM and returns the first element with the matching id. IDs should be unique, so it should be the only element with that ID. Note: the '#' is not necessary. 
document.getElementById('someId')


// Multiple elements
// document.querySelectorAll() gets multiple elements of the matching tag or class 
// It returns a NodeList, which can be iterated over with .forEach() and for loops. 
document.querySelectorAll('div')

// document.getElementsByTagName() and document.getElementsByClassName() get every element by the matching tag/class.
// They both return HTML collections which can only be iterated over with for loops.
document.getElementsByTagName()
document.getElementsByClassName()

```

## Changing and Creating DOM Elements
Once a DOM element is selected, there are several ways of changing the content in that Node.

```
const div = document.querySelector('div')

// Text content returns the full text of a node. It's less performance heavy and works for all nodes. 

div.textContent = 'some text'


// Inner text only grabs visible text, is performance heavy, and only works on HTML elements
div.innerText = 'some text'

// document.createElement() creates a new element when provided a tag name
// A created element can be set with text content just as a element selected by the DOM can.
const newDiv = document.createElement('div')
newDiv.textContent = 'my text'

// innerHTML can add HTML content to an element. Use of this should be limited as it's slow, it clears out everything, removes event listeners, and most importantly, it's vulnerable to cross-site-scripting attacks

div.innerHTML = '<p>Use this with caution</p>'

```


## Removing elements
Once selected, elements can be removed in a couple ways.

```
// will remove the element
div.remove()

// will clear the element of all its nested children
div.innerHTML = ''

```