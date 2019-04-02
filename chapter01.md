# Your First Application

## Where to Start

In this book, we will cover the use of JavaScript in all its current incarnations (serverside,
scripting, desktop, browser-based, and more), but for historical and practical
reasons, we’re going to start with a browser-based program.

That said, my browser of choice is Firefox, and in
this text, I will discuss Firefox features that will help you in your programming journey.

The two most popular textmode
editors are vi/vim and Emacs. One big advantage to text-mode editors is that,
in addition to using them on your computer, you can use them over SSH—meaning
you can remotely connect to a computer and edit your files in a familiar editor. Windowed
editors can feel more modern, and add some helpful (and more familiar) user
interface elements.
Popular
windowed editors are Atom, Sublime Text, Coda, Visual Studio, Notepad++, TextPad,
and Xcode.

## A Comment on Comments

In JavaScript, there are two kinds of comments: inline comments and block comments.
An inline comment starts with two forward slashes (//) and extends to the
end of the line. A block comment starts with a forward slash and an asterisk (/*) and
ends with an asterisk and a forward slash (*/), and can span multiple lines. Here’s an
example that illustrates both types of comments:

```javascript
console.log("echo"); // prints "echo" to the console
/*
  In the previous line, everything up to the double forward slashes
  is JavaScript code, and must be valid syntax. The double
  forward slashes start a comment, and will be ignored by JavaScript.
  This text is in a block comment, and will also be ignored
  by JavaScript. We've chosen to indent the comments of this block
  for readability, but that's not necessary.
*/
/*Look, Ma, no indentation!*/
```

Cascading Style Sheets (CSS), which we’ll see shortly, also use JavaScript syntax for
block comments (inline comments are not supported in CSS). HTML (like CSS)
doesn’t have inline comments, and its block comments are different than JavaScript.
They are surrounded by the unwieldy <!-- and -->:

```html
<head>
   <title>HTML and CSS Example</title>
   <!-- this is an HTML comment...
            which can span multiple lines. -->
   <style>
      body: { color: red; }
      /* this is a CSS comment...
         which can span multiple lines. */
   </style>
   <script>
      console.log("echo"); // back in JavaScript...
      /* ...so both inline and block comments
         are supported. */
   </script>
</head>
```


## Getting Started

We’re going to start by creating three files: an HTML file, a CSS file, and a JavaScript
source file. We could do everything in the HTML file (JavaScript and CSS can be
embedded in HTML), but there are certain advantages to keeping them separate. If
you’re new to programming.

One last important note about this chapter. This is the lone chapter in the book in
which the code samples will be written in ES5 syntax, not ES6 (Harmony). This is to
ensure that the code samples will run, even if you aren’t using a browser that has
implemented ES6. In the following chapters, we will talk about how to write code in
ES6 and “transcompile” it so that it will run on legacy browsers.

Let’s start with the JavaScript file. Using a text editor, create a file called _main.js_. For
now, let’s just put a single line in this file:

```javascript
console.log('main.js loaded');
```

Then create the CSS file, _main.css_. We don’t actually have anything to put in here yet,
so we’ll just include a comment so we don’t have an empty file:

```css
/* Styles go here. */
```

Then create a file called _index.html_:

```html
<!doctype html>
<html>
   <head>
      <link rel="stylesheet" href="main.css">
   </head>
<body>
   <h1>My first application!</h1>
   <p>Welcome to <i>Learning JavaScript, 3rd Edition</i>.</p>

   <script src="main.js"></script>
</body>
</html>
```

An HTML document consists of two main
parts: the head and the body. The head contains information that is not directly displayed
in your browser (though it can affect what’s displayed in your browser). The
body contains the contents of your page that will be rendered in your browser. It’s
important to understand that elements in the head will never be shown in the
browser, whereas elements in the body usually are (certain types of elements, like
<script>, won’t be visible, and CSS styles can also hide body elements).
  
In the head, we have the line <link rel="stylesheet" href="main.css">; this is
what links the currently empty CSS file into your document. Then, at the end of the
body, we have the line <script src="main.js"></script>, which is what links the
JavaScript file into your document. It may seem odd to you that one goes in the head
and the other goes at the end of the body. While we could have put the <script> tag
in the head, there are performance and complexity reasons for putting it at the end of
the body.
  
In the body, we have `<h1>My first application!</h1>`, which is first-level header
text (which indicates the largest, most important text on the page), followed by a `<p>`
(paragraph) tag, which contains some text, some of which is italic (denoted by the
`<i>` tag).

## The JavaScript Console

We’ve already written some JavaScript: console.log('main.js loaded'). What did
that do? The console is a text-only tool for programmers to help them diagnose their
work. You will use the console extensively as you go through this book.

Different browsers have different ways of accessing the console. Because you will be
doing this quite often, I recommend learning the keyboard shortcut. In Firefox, it’s
Ctrl-Shift-K (Windows and Linux) or Command-Option-K (Mac).

In the page in which you loaded index.html, open the JavaScript console; you should
see the text “main.js loaded” (if you don’t see it, try reloading the page). console.log
is a method3 that will print whatever you want to the console, which is very helpful
for debugging and learning alike.

One of the many helpful features of the console is that, in addition to seeing output
from your program, you can enter JavaScript directly in the console, thereby testing
things out, learning about JavaScript features, and even modifying your program
temporarily.

## jQuery
We’re going to add an extremely popular client-side scripting library called jQuery to
our page. While it is not necessary, or even germane to the task at hand, it is such a
ubiquitous library that it is often the first one you will include in your web code. Even
though we could easily get by without it in this example, the sooner you start getting
accustomed to seeing jQuery code, the better off you will be.

At the end of the body, before we include our own main.js, we’ll link in jQuery:

```javascript
<script src="https://code.jquery.com/jquery-2.1.1.min.js"></script>

<script src="main.js"></script>
```

You’ll notice that we’re using an Internet URL, which means your page won’t work
correctly without Internet access. We’re linking in jQuery from a publicly hosted _content
delivery network (CDN)_, which has certain performance advantages. If you will
be working on your project offline, you’ll have to download the file and link it from
your computer instead. Now we’ll modify our _main.js_ file to take advantage of one of
jQuery’s features:

```javascript
$(document).ready(function() {
   'use strict';
   console.log('main.js loaded');
});
```

What jQuery is doing for us here is making sure that the browser has loaded all of the
HTML before executing our JavaScript (which is currently just a single console.log).
Whenever we’re working with browser-based JavaScript, we’ll be doing this just to
establish the practice: any JavaScript you write will go between the $(docu
ment).ready(function() { and }); lines. Also note the line 'use strict'; this is
something we’ll learn more about later, but basically this tells the JavaScript interpreter
to treat your code more rigorously. While that may not sound like a good thing
at first, it actually helps you write better JavaScript, and prevents common and
difficult-to-diagnose problems. We’ll certainly be learning to write very rigorous Java‐
Script in this book!

## Drawing Graphics Primitive

Among many of the benefits HTML5 brought was a standardized graphics interface.
The HTML5 canvas allows you to draw graphics primitives like squares, circles, and
polygons. Using the canvas directly can be painful, so we’ll use a graphics library
called Paper.js to take advantage of the HTML5 canvas.

Before we start using Paper.js to draw things, we’ll need an HTML canvas element to
draw on. Add the following to the body (you can put it anywhere; after the intro paragraph,
for example):

```html
<canvas id="mainCanvas"></canvas>
```

> 9 (33 / 364)


