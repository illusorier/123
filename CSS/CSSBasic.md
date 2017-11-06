## What is HTML?

HTML uses simple commands called *tags* to define the various parts of a web page.

At its heart,HTML is a fairly simple language made up of elements.

HTML is used to specify whether your web content should be recognized as a paragraph,list,heading,link,image,multimedia player,form,or one of many available elements or even a new element that you define.

HTML is not a programming language;it is a *markup* language,used to tell your browser how to structure the webpages you visit.

### Anatomy of an HTML element

The main parts of our element are:

1. **The opening tag**:This consists of the name of the element

## What is the HTML head?

The head of an HTML document is the part that is not displayed in the web browser when the page is loaded.

The head's job is to contain metadata about the document.

## Document Types

All web pages begin with a *doctype* - a line of code that identifies what flavor of HTML

## CSS

CSS is used to style and lay out webpages.

CSS is a language for specifying how documents are presented to users.

A **document** is usually a text file structured using a *markup language* - HTML is the most common markup language,but you will also come across other markup languages such as SVG or XML.

Web browsers apply **CSS rules** to a document to affect how they are displayed.A CSS rule is formed from:

- A set of properties,which have values set to update how the HTML content is displayed.
- A selector,which selects the element(s) you want to apply to updated property values to.

### How does CSS actually work?

When a browser displays a document,it must combine the document's content with its style information.It process the document in two stages

1. The browser converts HTML and CSS into the DOM.The DOM represents the document in the computer's memory.It combines the document's content with its style.
2. The browser displays the contents of the DOM.

## Selectors: Identifying What to Style

Every CSS style has two basic parts:a selector and a declaration block.

### Different types of selector

Selectors can be divided into the following categories

- Simple selectors
- Attribute selectors



### Styling Groups of Tags

Sometimes you need a quick way to apply the same formatting to several different elements.

### Styling Tags Within Tags

Choosing whether to style your page with type selectors or class selectors is a tradeoff.

Type selectors are fast and easy,but they make every occurrence of a tag look the same.

Class and ID selectors give you the flexibility to style individual page elements independently,but creating class or ID styles also requires you to add the appropriate class or ID to the HTML tags you wish to style.

What you need is a way to combine the ease of type selectors with the precision of classes and IDs.

You use descendant selectors to format a whole 

- Descendant: A tag inside
- Child: A tag that's directly enclosed by another tag is a child.

Descendant selectors let you take advantage of the HTML family tree

### Pseudo-Classes and Pseudo-Elements
Sometimes you need to select parts of a web page that don't have tags per se,but are nonetheless easy to identify,like the first line of a paragraph or a link as you move your mouse over it.

#### Styles for Links

Four pseudo-classed let you format links in four different states based on how a visitor has interacted with that link.

- a:link 
- a:visited
- a:hover
- a:active

#### Styling Paragraph Parts

CSS provides two pseudo-elements - `:first-letter` and `:first-line`.

#### More Pseudo-Classes and Pseudo-Elements

##### :Before

The `:before` pseudo-element does something no other selector can:It lets you add content preceding a given element.

##### ::placeholder

The `::placeholder` CSS pseudo-element represents the placeholder text of a form element.

##### :hover:before

## Saving Time with Style Inheritance

Inheritance is the process by which some CSS properties applied to one tag are passed to nested tags.

## CSS Transforms,Transitions,and Animations
For the short history of the Web,designers have had a few options for adding animation to their websites.

## Managing Multiple Styles:The Cascade

The cascade is a set of rules for determining which style properties get applied to an element.

### The Principles Of OOCSS

As with any object-based coding method, the purpose of OOCSS is to encourage code reuse and,

#### Separation of structure from skin

Almost every element on a styled Web page has different visual features (i.e. "skins") that are repeated in different contexts.

When these different features are abstracted into class-based modules, they become reusable and can be applied to any element and have the same basic result.

## Content categories

Each HTML element must abide by rules defining what kind of content it can have

##### line-height

On block level elements, the *line-height* property specifies the minimum height of line boxes 

The `line-height` property defines the amount of space above and below inline elements 

This property is most often used to set the leading for lines of text. 

The `line-height` property can accept the keyword values `normal` or `none` as well as a number, length, or percentage.

The recommended method for defining line height is using a number value, referred to as a "unitless" line height.

#### text-align

The text-align CSS property describe how inline content like text is aligned in its parent block element.text-align does not control the alignment of block elements,only their inline content.

#### box-shadow

The `box-shaodw` property describes one or more shadow effects as a comma-separated list.

Specify a `box-shadow` using:

- Two

##### Values

Pure CSS-based layouts.

One of the somewhat frustrating properties of CSS is the fact that elements only stretch vertically as far as they need to.



