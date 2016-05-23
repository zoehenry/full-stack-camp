<img src="https://www.codesail.io/assets/logo-3f332da93aa10ae55f53d3098586def01c2219d425dbe57591a2312c13476eeb.png" style="width: 75px;"/>

# HTML/CSS Primer

##### 2016 CodeSail Bootcamp
Revised May 22, 2016

---
## Introduction: Web Development and Websites
When you go to a website and see its contents, a series of processes are happening very quickly in sequence:

<img src="http://i.imgur.com/M5JhIvt.png" />

- You type a web address into your browser (HTTP Request: "I want to go the main page.").
- Your Internet Service Provider (e.g., Comcast, AT&T) takes you to the server's address (the address of a computer that lives in someone’s garage or owned by a company).
- The server reads your request ("I want to go to the main page.").
- The server grabs the relevant information.
- The server serves you HTML, CSS, and Javascript information (HTTP Response: "Here is what this main page contains.").

In the very last step, the server returns HTML, CSS, and Javascript information to tell your browser how to render its information. In other words, HTML, CSS, and Javascript make up the appearance of the web page you requested.

In this primer, we will go over the fundamental elements of HTML and CSS as an introduction to making your very first web page.

## Fundamentals of HTML

A markup language is a system for 'marking' a document so that it can be differentiated from text. A markup language is a set of markup tags and their properties. One such markup languages is the HyperText Markup Language (HTML), which is the standard markup language for websites.

It has 2 fundamental structures: elements and their attributes.

#### Element

An element consists of a starting and ending tag (except in cases of self-closing tags) and the content that sits between the start (e.g., `<html>`) and end tags (e.g., `</html>`).

Some common elements include:
- `<html>`

  This tag defines to the browser that the document is a HTML document. All HTML documents start with this tag.

- `<head>`

  This tag is used to tell the browser that the content include a title for the document, scripts, styles, meta information, and more. This is useful for web crawlers, like Google, to know what kind of website the page is without having to parse through the entire site.

- `<body>`

  The `body` element contains all the contents that are 'visible' to the user; the contents of an HTML document, such as text, hyperlinks, images, tables, lists, etc.

- `<div>`

  This tag defines a section in an HTML document.

- `<link>`

  This tag defines the relationship between a document and an external resource -- either within the same file system or remote. It is commonly used to link stylesheets.

- `<script>`

  The `script` element is used to define a client-side script, most commonly Javascript scripts.

There are many more elements to utilize, and they'll come into your toolbox with experience and time.

#### Attributes

Attributes describe an element, providing additional information about it, and are specified in the start tag of an element. Some attributes can be global, which can be used with any HTML element.

Some common attributes include:

- `class` (global attribute)

  Example: `<div class="faq-section answer">...</div>`

  A `class` is a space-separated list of the classes of the element. It is used to distinguish an element from another class.

- `id` (global attribute)

  Example: `<div id="faq-section answer">...</div>`

  An `id` is a unique identifier (ID) which must be unique in the whole document. Its purpose is to identify the element when linking (using a fragment identifier), scripting, or styling (with CSS). Unlike `class`, an `id` is unique: Each element can have only one ID, and each page can have only one element with that ID. This has fallen out of conventional favor, but you may still see it in websites.

- `href`

  Example: `<a href="http://google.com">Link to Google</a>`

  The `href` attribute specifies the link's destination.

Example HTML:
```
  <html>
    <head>
      <link rel="stylesheet" href="mystyle.css">
    </head>
    <body>
      <div class="title">
        <h1>Hello World!</h1>
      </div>
      <div class="description">
        <p class="first-paragraph">This is a paragraph of text.</p>
        <p>Now back inside the p.</p>
        <p>This is a description of our hello world page.</p>
      </div>
      <div class="links">
        <p>Here is <a href="http://google.com">My favorite search engine</a>.</p>
        <a href="http://twitter.com">My favorite microblog</a>.
      </div>
      <div class="images">
        <img src="https://www.petfinder.com/wp-content/uploads/2012/11/140272627-grooming-needs-senior-cat-632x475.jpg">
      </div>
    </body>
  </html>
```

## Fundamentals of CSS

Cascading Style Sheets (CSS) is a stylesheet language used for describing the presentation of a document written in a markup language, like HTML. Like a markup language, there is a particular syntax to use. This separation of HTML and CSS in two separate systems allows developers to decouple content from presentation, so as to modularize their development.

CSS consists of 2 fundamental structures: selectors and declarations.

#### Selectors
Selectors point to 'select' an element, class, or id from your HTML document. Declarations modify the selected HTML element using [CSS properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference).

<img src='http://www.w3schools.com/css/selector.gif'>

##### Selecting an element

```
p {
  color: red;
}
```

##### Selecting a class

```
.description {
  background-color: red;
}
```

##### Selecting an id

```
#faq1 {
  color: red;
}
```

#### Common declarations

- `display` The display CSS property specifies the type of rendering box used for an element. Common values for `display` are:
  - `inline` - content in this declaration appear inline and won't take up more space than its content needs
    - <img src="http://imgur.com/Cm9rAon.png" width="150px">
  - `block` - content in this declaration will take up as much width and height as indicated. If width and height are undefined, it will default to 100% width and the height of the content.
    - <img src="http://i.imgur.com/BZ2wP6J.png" width="150px">

  Example:
  ```
  .description {
    display: block;
  }
  ```

- `width` This declares the width of an element.

  Example:
  ```
  .description {
    display: block;
    width: 400px;
  }
  ```
- `height` This declares the width of an element.
  Example:
  ```
  .description {
    display: block;
    height: 400px;
  }
  ```
- `margin` This declares the margin for all four sides of an element. Its values are denoted as the margin for bottom, left, right, and top, respectively.

  Example:
  ```
  .description {
    display: block;
    height: 400px;
    margin: 20px 0px 0px 20px;
  }
  ```

- `padding` The `padding` property sets the space between the content of the element and its border. Its values are denoted as the padding for bottom, left, right, and top, respectively.
  Example:
  ```
  .description {
    display: block;
    height: 400px;
    margin: 20px 0px 0px 20px;
    padding: 20px 0px 0px 0px;
  }
  ```
- `text-align` describes how inline content like text is aligned in its parent block element.

  Example:
  ```
  .description p {
    text-align: center;
  }
  ```
- `background-color` describes the background color of an element.

  Example:
  ```
  .description {
    background-color: red;
  }
  ```
- `background-image` describes the background image of an element.

  Example:
  ```
  .description {
    background-image: url("http://ideatube.science/wp/xMZaTGd.jpg");
  }
  ```
- `background-repeat` denotes how the background of an element would repeat. By default, the background will repeat vertically and horizontally. Sample values: `repeat-x`, `repeat-y`, `no-repeat`

  Example:
  ```
  .description {
    background-image: url("http://ideatube.science/wp/xMZaTGd.jpg");
    background-repeat: no-repeat;
  }
  ```
- `background-size` describes the size of the background image. Sample values: `80px 60px`, `cover`

  Example:
  ```
  .description {
    background-image: url("http://ideatube.science/wp/xMZaTGd.jpg");
    background-repeat: no-repeat;
    background-size: cover;
  }
  ```

#### Grouping selectors

If there are elements, classes, or ids that share similar declarations, they can be grouped:

```
p, .description {
  color: red;
  background-color: blue;
}
```

Example CSS

```
  body {
    background-color: yellow;
  }

  .title {
    color: red;
  }

  h1, p {
    font-family: sans-serif;
  }

  div.description p.first-paragraph {
    font-size: 100px;
    border: 1px black solid;
    background-color: white;
    padding: 10px;
    margin: 100px;
  }

  .images {
    text-align: center;
  }
```

## Exercise: Create a website

It is highly recommended that you complete this exercise in a text editor like [Sublime](https://www.sublimetext.com) or [Atom](https://atom.io).

1. Modify the [practice HTML and stylesheet documents](https://github.com/codesail-camp/full-stack-camp/tree/master/week-0/part-2-practice) from the part-2-practice folder to include information about yourself.
  - To view the webpage, open `practice.html` in your browser.


## Homework:
##### Due Friday, May 27, 2016
- Using the image and HTML skeleton provided in the [exercise folder](https://github.com/codesail-camp/full-stack-camp/tree/master/week-0/part-2-exercise), create a webpage to look like the image. You may need to refer to documentation on [CSS properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference). It is highly encouraged that you use external references to complete this assignment!
