# Web Programming

This is some sample text.

(section-label)=
## HTML Basics

What is HTML? HTML stands for HyperText Markup Language, and is a language that tells your browser how the page should be structured. The language
is made up entirely of elements, which each act differently to create a cohesive web page. For the most part, each element starts with an opening 
tag, has some content inside, and then ends with a closing tag.

An element may look like this:

```
<p> 
    This is the content. 
</p>
```

Opening tags follow this format: ```<tagName>``` 
while closing tags look like this: ```</tagName>``` 

It is important to know that when it comes to spacing, HTML will ignore anything more than a single space. So the following two options will produce
the same output:

```
<p>
    This is an option for formatting code.
</p>
```
and
```
<p> This is an option for formatting code. </p>
```

To start writing in HTML, we first wnant to tell the document that we are going to be writing HTML. We do this with a very simple line: ```<!DOCTYPE html>```.
This goes at the top of every HTML file. Then, to further let the document know that we are writing HTML code, we make an ```<html>``` tag. All of the other 
elements we create will go inside the html tag.

Then, we want to have some more structure, so we will set up the layout for our page with two very simple tags, ```<head>``` and ```<body>```. The head tag will
hold all of the information about the page, like styles, and imports, while the body will hold the actual content. All together, a very simple web page may look something like this:

```
<!DOCTYPE html>
<html>
    <head>
    </head>

    <body>
        <p> Hello World! </p>
    </body>
</html>
```

(section-label)=
## Tag Types

Now, we know everything needed to make a website. A very very boring website, but a website nonetheless. In order to create more interesting pages, we need to know
more about how to format text. Sometimes, the tag you put the text in is all you need. While really any tag can be used for any purpose, it helps to organize and simplify your web pages if you are strategic about the tags you use and when. Each tag has built in properties that make it more or less adventageous depending on your need.

For example, take the ```<div> </div>``` tag for example. The ```<div>``` tag is a **block level element**. This means that the ```<div>``` tag by default takes up the entire page in width, despite what is inside. Any other elements after the div will appear under it. For example, imagine we have a code segmenth that looks like this:

```
<div>Text 1</div>
<div>Text 2</div>
<div>Text 3</div>
```

This will appear as:

Text 1<br>
Text 2<br>
Text 3<br>

All block level elements, such as ```<div>```s, share common properties. They all start on a new line, take up as much horizontal space as possible, and works with certain style properties such as width, height, and both vertical and horizontal margins. But we'll talk more about those properties later.

In contrast, there are also **inline level elements**. For example, the ```<span></span>``` tag. By default, the ```<span>``` tag is only as wide as the text or other tags it contains, and they appear next to any other elements in the line. For example, imagine we have a similar code segment to before that looks like this: 

```
<span>Text 1</span>
<span>Text 2</span>
<span>Text 3</span>
```

This will appear as:

Text 1 Text 2 Text 3

Unlike block level elements, the inline 

(section-label)=
## Images

(section-label)=
## Links

(section-label)=
## Lists

(section-label)=
## Tables

(section-label)=
## Forms

(section-label)=
## Structure Tags

(section-label)=
## Internal Styles

(section-label)=
## External Styles
