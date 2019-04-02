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


