# Objectives

By the end of this tutorial, you'll understand how websites are created, served, and rendered. We will go through a general overview of HTML and CSS and how JavaScript relates to those technologies. We will also discuss the current state of web development and 

## HTML

HTML (**H**yper **T**ext **M**arkup **L**anguage) is a language that allows us to add structure and meaning to text. Every website you use on a daily basis is being served to your browser through HTML. When you make a request to a certain URL such as https://www.lehigh.edu, a server somewhere processes that request and serves the appropriate HTML content to your browser (Chrome, Safari, Firefox, etc.) which is responsible for rendering it in a consistent and standard way. We'll talk more later about why browsers display things the way they do and what kind of control we have over that process.

Here is an example of an HTML response from a website we should all be familiar with:

```
<div class="promo-content left">
    <div class="flag">
        <h2>Our College Town</h2>
    </div>
    <h3 id="bethlehem-header">Explore Bethlehem and the Lehigh Valley</h3>
    <p>Located in the heart of the beautiful Lehigh Valley, Bethlehem is a vibrant city, rich in history and culture and known for its small-town friendliness and feel.</p>
    <div class="btn adm-promo-btn">
        <a aria-labelledby="bethlehem-link bethlehem-header" href="/about/bethlehem" id="bethlehem-link">Learn more</a>
    </div>
</div>
```

When rendered by the browser, that code produces the following result:

![Result](explore_bethlehem_snippet.png)

This code might seem overwhelming at first, but we can break it down into just a few simple parts.

### Elements and Tags

HTML is comprised entirely of things called elements. An example of an element in the above code would be `<h2>Our College Town</h2>`. The `<h2>` and `</h2>` parts are referred to as *tags*. Tags contain identifiers (`h2` in this case) that represent a particular type of content. `h2` is a **2**nd level **h**eading tag. The opening tag will always consist of a `<`, the tag name, and `>`. The closing tag will always consist of `</`, the tag name, and `>`.

Throughout this tutorial, I'll tend to use the words `tag` and `element` interchangeably. They are different, but I generally do mean the same thing when I'm referring to either. My interpretation is that an element is a specific instance of a tag along with its data, whereas the tag is simply the tag/identifier on its own.

Now, let's look at another element. `<h3 id="bethlehem-header">Explore Bethlehem and the Lehigh Valley</h3>` is an example of an element that contains additional data about the content. We can see that this element has a tag name of `h3`. Just like the last element we looked at, it's a heading, but this time it's a level 3 heading which means it will generally be rendered slightly smaller and have less overall importance than `h2`.

We can see that this element is also given an ID. `id="bethlehem-header"` tells us that this element has an ID of "bethlehem-header." We'll talk more later about what that can be used for. In this case, `id` is referred to as an attribute. Elements can have a variety of attributes. Some others in the example above are `class`, `href`, and `aria-labelledby`.

Each element has a set of attributes that we can set. Some are common throughout all elements such as `id`, `title`, and `class`, while others are specific to their elements.

### Document Structure

Next, let's look at the structure of a whole HTML document:

```
<!DOCTYPE html>
<html>
    <head>
        <title>Example</title>
    </head>
    <body>
        <h1>This is an example</h1>
        <p>It is very helpful</p>
    </body>
</html>
```

First of all, we see something pretty weird. `<!DOCTYPE html>` looks different from all of the other tags. I'm not sure why that's a standard, but it is pretty self explanitory. It just lets the browser know that we're looking at a modern HTML document. 

Below that, we see the `html` tag. This wraps all of the other tags, and that's pretty much all there is to it. Inside, we see the `head` tag. The `head` doesn't actually get rendered by the browser. In there we provide information about the document including the title, metadata, and as we'll see later on, this is where we will include certain outside resources that our page will depend on.

The `body` tag is where all of the page's visual content will be stored. That's where we'll put our structural and semantic elements like `header`, `main`, and `footer`, and also where all of the other tags like `p`, `h1`-`h6`, and pretty much all of the other tags we'll talk about today.

### Useful Tags

There are *a lot* of HTML tags we could talk about. I don't think it would be very helpful for me to list off all of the tags you might need to know, so I'm just going to go over a few useful ones. As you learn HTML, Google is your friend. Look up how to do stuff, reference sites like [w3schools.com](https://www.w3schools.com/TAGS/default.ASP), and look at the source code of your favorite websites. I've been working with HTML for years now, and I'm still discovering new elements regularly. 

Tag Name | Description          | Example
---------|----------------------|--------
 a       | Hyperlink            | `<a href="/home">Home</a>`
 button  | Button               | `<button>Click me!</button>`
 p       | Paragraph            | `<p>This is a paragraph</p>`
 h1-h6   | Headings             | `<h1>Page title</h1>`
 div     | Generic container    | `<div><p>Paragraph in div!</p></div>`
 section | Section of document  | `<section id="chapter-one">...</section>`
img      | Image/graphic        | `<img src="explore_bethlehem_snippet.png">`

Some other concepts you could look into on your own are the `form` tag and the associated form elements (`label`, `input`, `textarea`, `select`), the `table` tag and its family of tags (`thead`, `tbody`, `tr`, `th`, `td`), and additional semantic tags (`header`, `main`, `footer`, `aside`, `nav`).

### Semantic HTML

When I say *semantic*, what I'm talking about is a tag that has a specific meaning associated with it. The way I see it, all tags have some meaning (even if that meaning is that it doesn't have any), and semantic HTML is just HTML where the meaning is being actively considered. For example, `h1` should be the top level heading on the page. This means that it describes what the entire document is about. `p` is a paragraph tag, so it should contain paragraph text, not navigation, title text, or even other paragraphs.

By writing semantic HTML, we make it easier for search engines like Google to crawl and index our websites. We also help people with screen readers to navigate our websites. This is an extremely important aspect of web development that should not be overlooked. 

[Here's an example of some nice semantic HTML](examples/example_0.html)

Notice that the header of the website is within the `header` tag, the main content is wrapped in `main`, unique sections appear in `sections`, and there's even a sidebar (not on the side yet) in an `aside` tag. We also see `nav` being used to store navigation links to the sections within the page as well as some other interesting tags like `figure`, `figcaption`, and `blockquote`.

Also take a look at the way the links work in that document. Run the document in your browser if you can, and you should see that clicking on the links with `href` equal to `#abc` will scroll to the element with the `id` equal to `abc`.

If you opened up that website in your browser, you probably realized that it's **very** ugly. Next, we'll talk about how you can make it look better.

## CSS

So far, you've learned how you can structure a web page and what that structure actually means. Now, we're going to dive into the specifics of making a page look the way you want it to. Web pages are styled using a language called CSS. CSS (**C**ascading **S**tyle **S**heets) allow us to define the colors, fonts, spacing, animations/movement, and certain interactive behaviors associated with elements and groups of elements.

Let's look at that sample HTML from the Lehigh website again:
```
<div class="promo">
    <div class="promo-content left">
        <div class="flag">
            <h2>Our College Town</h2>
        </div>
        <h3 id="bethlehem-header">Explore Bethlehem and the Lehigh Valley</h3>
        <p>Located in the heart of the beautiful Lehigh Valley, Bethlehem is a vibrant city, rich in history and culture and known for its small-town friendliness and feel.</p>
        <div class="btn adm-promo-btn">
            <a aria-labelledby="bethlehem-link bethlehem-header" href="/about/bethlehem" id="bethlehem-link">Learn more</a>
        </div>
    </div>
</div>
```

Now, here's some of the CSS that goes along with that:
```
...
.promo .promo-content {
    padding-top: 20px;
    padding-bottom: 30px;
    background-color: rgba(255,255,255,.95);
    margin: 0;
    width: 370px;
}
.promo h3 {
    color: #502d0e;
    margin: 20px 30px 15px;
    font-family: "Merriweather";
    font-weight: 500;
    font-style: italic;
    font-size: 1.4em;
}
...
```

Take note of the structure of this CSS. There's what's called a *selector* (`.promo .promo-content`, `.promo h3`) followed by a *block* that lists *properties* and their *values*. 

### Including CSS

Most of the time, you'll find CSS in an external file like `styles.css`. These files can be included from within the `head` section of your HTML document using the `link` tag like so: `<link rel="stylesheet" href="style.css">`

CSS can also be included within `style` tags, also generally found in the `head` section of the document.

It's also possible to include styles directly onto an element. For example `<h1 style="font-size: 100px">BIG</h1>`. Styles attached to an element through the `style` attribute are referred to as *inline*.

### Selectors

A selector does exactly what you might imagine: it selects an element or a group of elements. There are many ways to do this, so let's just go over a few.

To select an element by its `id` attribute, you can use `#` followed by the id (just like we saw earlier with `href`).

Select the element with the id "main-header"
```
#main-header {
    ...
}
```

To select elements that have a particular class, use a `.` followed by the class name.

Select anything with the class of "section-content"
```
.section-content {
    ...
}
```

To select all elements with a particular tag name just use the tag name.

Select all `h2` elements.
```
h2 {
    ...
}
```

You can also combine selectors. `h2.main-heading` selects all `h2` tags with a class of `main-heading`. `div .main-heading` selects all elements with the class of `main-heading` that are inside of a `div`. 

It's also possible to select multiple elements that aren't related. `h2, h3` selects both `h2` and `h3` elements.

### Properties

Inside of the block (the curly braces) you'll find a ton of different properties. As with the HTML tags, there are way too many to go over in this short tutorial, so I'll just cover a few. In general, though, the syntax is consistent for all property-value pairs. You'll have the name of the property, `:`, then the value. The format of the values can vary slightly, but most often they'll be in the form of a number with a unit (`10px`, `50%`, `12pt`), a color (`red`, `#f00`, `rgb(255,0,0)`), or a specific pre-defined value (`block`, `italic`, `bold`). 

Make sure you include a semicolon after the value of each property.

### Useful Properties

Property       | Description          | Example
---------------|----------------------|--------
 color         | Text color           | `color: black;`
 background    | Background content   | `background: #fff;`
 font-family   | Font style/family    | `font-family: sans-serif;`
 font-size     | Font size            | `font-size: 14pt;`
 text-align    | Text alignment       | `text-align: center;`
 margin-(top, right, bottom, left) | Space outside the element on the specified side. | `margin-left: 10px;` 
 margin        | Shorthand for margin -top, -right, -bottom, -left | `margin: 10px 20px 10px 30px;`
 padding-(top, right, bottom, left)| Space within element on specified side | `padding-top: 10px;`
 padding        | Shorthand for padding -top, -right, -bottom, -left | `padding: 10px 20px 10px 30px;`

### Cascading and Inheritance

This is where things get a little bit tricky with CSS. The "cascading" part of the name refers to the fact that properties can conflict with and override properties from other selectors. If you style a paragraph to have red text, then later style that same element to have white text, the text will be white. Order matters and CSS is processed from top to bottom, so declaring the same property multiple times will result in the second one being chosen. 

It isn't always that simple, however. If you select an element multiple times but one is more specific, the more specific selection will prevail. For example, `h1#page-title` is more specific than `h1` and would override it.

Another important aspect of CSS is *inheritance*. HTML elements inherit the CSS of their parents. Giving the `body` a text color of `red` will result in all elements inside having red text by default. If you then declare a paragraph in the body to have blue text, your selection of `p` is more specific than the `body`'s rule that it's inheriting, so the `p`'s color will be blue.

This may be a little bit confusing at first, but I promise you'll get much better at it with practice.

[Here's that example from before, but now with some CSS](examples/example_1.html)

There are definitely some properties and concepts that we didn't cover in this example, but CSS is something that I believe you can only learn by doing. It can be frustrating, but after the 10th time you turn to Google or Stack Overflow for answers, it will start to stick :)