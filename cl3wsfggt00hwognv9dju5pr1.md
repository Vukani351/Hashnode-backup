---
title: "A Simple HTML Basics Cheatsheet"
seoTitle: "learning programming | basic html | html | basic programming | webdev"
seoDescription: "this is a personal web dev beginner guide with html, showing the basic tags and the basics of how html orks"
datePublished: 2022-06-02T09:01:01.039Z
cuid: cl3wsfggt00hwognv9dju5pr1
slug: html-cheatsheet
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1654063784328/Hd8_tYTiD.png
tags: webdevelopment, webdev, html5, programming-languages, programming-tips

---

# BASIC HTML:

The structure for writing HTML code is using tags to tell the browser what it's interpreting for you the user.

<div align="center">


![@nqubekogcabashe html basics image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jj1pb3tvw0w8wyhoo3c3.png)

</div>


## Creating HTML File:


Creating the html file means creating a file with the ` .html ` extension.


## Basic Tags:

<div align="center">

![@nqubekogcabashe html basic tags](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2atagbmas50hcpkyw2oa.png)
</div>

- HTML tag is the one that will initialize / format the HTML document for the browser.

```html
    <html>

        // Your other tags will go here

    </html>

```

- head tag is where we put tags and meta-tags that will describe the HTML document.
<div align="center">

![@nqubekogcabashe html head tag](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ic0d12iwws84u3wzi1b8.png)
</div>

- the head tag goes inside the `<html></html>` tag but it's one tag whose content you won't see displayed on the HTML, but perhaps in the window.

<div align="center">

![@nqubekogcabashe head tag img](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8r14shmw6u4hl6dxy0v0.png)
</div>

```html
    <head> 
        // code for other tags and meta-tags goes here
    </head>

```

- title tag is used to give a name to the window or tab that will represent that page.

```html
    <title> 
        // page title goes here
    </title>
```
- body tag is used to contain the web page's content, this is where you put all content.


```html
    <body> 
        //web page content goes here
    </body>

```

## Body Tag Attributes Examples:

<div align="center">

![@nqubekogcabashe html body tag](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mp60dl9jvq5qy0ty4aiv.png)
</div>

- to set the background color to green of body tag. You can use the color name or hex value

> `html <body align="center" bgcolor="green"> ... </body>   `

- to set the text color of links, using the name or hex value:

> ` <body align="center" alink="green"> ... </body> `

- to set the color of visited links, using the name or hex value:

> `html <body align="center" alink="green"> ... </body>    `


## Text Tags:

These tags are used to format text content you adding to your HTML and you use the following HTML tags.
------------------------------------------------------------------

- to create pre-formatted text.

> ` <pre> ... </pre> `

- to create header tags h1, h2...h6 where the h1-largest & h6-smallest:

> ` <h1> Heading Text </h1> `

- to make text bold:

> ` <b> test to turn bold </b>  `

- to display/define source code usually monospace:

> ` <code> ... </code>  `

- to emphasize a word or text:

> ` <strong> ... </strong>  `

- to set the size of the font, replace "?" with size in em, rem, % or px as measurement:

> ` <font size="?"> ... </font> `

- to display source code:

> ` <body> ... </body> `

## Formatting:

We use these methods to group certain content types like articles, and containers like div spans.
------------------------------------------------------------------


## Container tags:

these tags are used to contain other tags or content within them, you would do this to create some sectioning, to be able to share attributes "style, format" or other reasons you intend for data to be suctioned out.

- We commonly use the div tag most times `  <div>...</div>   ` and within this tag, we add content that will be sections with many lines.

- We also use the span tag to create sections within divs also `    <span> ... </span>  ` and its used to format inline content with CSS.

- We then have the ` <p>... </p> ` to contain content within this paragraph tag as one paragraph.

### Html Input Tags:

> ` <input type="email" name=? value=? disabled=? /> ` 

- This is our basic input tag where the type attribute will have a value of either *email*, *password*, *number*, *URL* or *text* "I think there is more" but that's the ones I have used, but these are used to validate your input and also helps the reader understand the data they are expected to give the web page.

- Another that i have encountered include ` <input type='date/month/week/time name='date' /> ` and this one is used to input to date.
- Another good one is ` <input type='search' name='search' /> ` that is used for search.
- Another fun one i loved was ` <input type="color" value="green" /> `

- We also have the *name* attribute that will help you identify the input tag with the name attribute in situations with more than one input.

- Then we also have the *value* attribute that is used a lot to capture the input that you have put into the input tag.

- We also have the *disabled* attribute which determines if the input is accessible in terms of adding data.

So that's the basics of HTML I got time to write out but there are definitely more tags out there and your job is to seek them out and use them to your advantage to make the site user-friendly and lovable. 

------------------------------------------------------------------

I hope this helped you out and this is also another more details source for the [documentation ](https://devdocs.io/html/)for HTML please use it and also check out my video & content on how to use [documentation ](https://dev.to/nash4253/things-i-wish-i-knew-before-being-an-junior-dev-learning-3aej)using python example.
------------------------------------------------------------------