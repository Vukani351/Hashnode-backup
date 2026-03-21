---
title: "Debugging Tips: Javascript"
seoTitle: "debugging javascript | debugging with chrome | chrome dev tools"
seoDescription: "This is a post sharing the basics of using chrome for debugging javascript and helping you see the state of your code as you code along."
datePublished: 2022-04-26T06:19:00.126Z
cuid: cl2frcl2t01tky8nv3067680n
slug: debugging-tips-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/unsplash/i25aqE_YUZs/upload/v1650952147243/3gEd1bXTO.jpeg
tags: chrome, debugging, bugs-and-errors

---

Debugging is a developer's process to remove wrong logic or even incorrect syntax in their code. We will spend huge amounts of time debugging code, and if it's done incorrectly will consume more time than it should.

Let's discuss how to debug Javascript on chrome ‘will apply to other browsers too’ dev tools and also using vs code and how this can increase your productivity, mind you there are other debugging tools out there for other languages, and I am just trying to express what I have learned with chrome tools but all IDE's have a debugger and each language has a method for debugging you must search the net or just ask your seniors. 

This really helps me get more confident with my javascript and this is just a start, I am still learning some more.

## Chrome Developer tools “other browsers have it too”

Chrome developer tools are a part of the browser that allows you to debug code, see the structure of your HTML code with its CSS styles and how they affect it visually, and you can also interact with the behavior of your project on the browser. To open chrome developer tools on windows we can compound the command **ctrl + shift + I** 
Or you can go to the top-right corner and press the settings, then press the more tools option then select the Developer Tools option then we will have access to developer tools but only write do Javascript code on the console tab

![https://www.linkedin.com/in/nqubeko-gcabashe/](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vw4qodb4cjtp4re9jlwa.jpg)
> Visually showing you how to access the chrome dev tools.

### Console Object:

Using console object for debugging is common for developers, we can console log objects at run time to see what is in them, create a console warning or error to handle thrown errors or we can display objects so we can find exactly the key, value pairs in them, let's go through them.

We can use console.log to log strings, numbers, objects even HTML elements on the console as follows and it will pop up the options you have and if you have saved a variable:
![https://www.linkedin.com/in/nqubeko-gcabashe/](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/k2lnj1kzexvv39xql2xt.jpg)

We can also use console.log({ Object }) and put the object within brackets so it prints as an object or use the %[console.dir] method to see object with elements in it but this illustrates. It comes without saying that the object elements will be accessible using the dot operator.


![https://www.linkedin.com/in/nqubeko-gcabashe/](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/242ky2t9juevaugoiylh.jpg)
> 1. this example shows you how to initialize a variable 'or use one from your js which is running with that page'.
> 2. use the %[console.log({obj})] function with an object in brackets as params or you can use %[console.dir(obj)] and you can also witness the properties of that object you logging.

For times you wish the code to log an error or a warning, we have those options too, using the command %[console.error(TheErrorString)] & the %[console.warn(TheWarnString)].

![https://www.linkedin.com/in/nqubeko-gcabashe/](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/4o2dspa8gpkup4m4en0a.jpg)

You can also grab dom elements and log them to the console in situations you want to see which properties of that object are accessible or even use XML using **console.dirxml(obj)** or object format using **console.dir(obj)**.

![https://www.linkedin.com/in/nqubeko-gcabashe/](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/q429repjt22k08phh4ae.jpg)

> This image illustrates that **console.log(element)** will return to you a printed HTML element and you can see its structure and only its children but
console.dir will return the element's properties with their values which is more powerful.

We can also print out a group of statements or something like a 
stack trace of where a problem might be or something else using **console.group**, followed by **console.info** and console.group.

![https://www.linkedin.com/in/nqubeko-gcabashe/](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/au7gfefwqhvkvlepczly.jpg)

We also have %[console.table(Object)] which will take an object or % [console.table({obj1, obj2, objN})] and return it as a table format. Which is useful for seeing objects or data formatted properly.

![https://www.linkedin.com/in/nqubeko-gcabashe/](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/tgv35hwa784qe0wlpn2e.jpg)
> For this image we see the use of the table function using one object and another using two data objects.

### Using Break Points

We use breakpoints for situations where the code is resulting in something unexpected, so it's best to see the behavior while the code is on compile time. So let's look at what it looks like or works.

![https://www.linkedin.com/in/nqubeko-gcabashe/](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/azm0813sm6oxght6l8x4.jpg)
> So what we have at line 13 is what we call a log message and it logs a message to the console when code execution reaches that line, and line 14 is in fact our breakpoint you just add by clicking the space between the border and line number.

![https://www.linkedin.com/in/nqubeko-gcabashe/](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/v1d30dm4yu6d9u6pgevp.jpg)
> Here we can see the total breakpoints in the project and also the ones which are visible on that file.

So as soon as you make these breakpoints on where you want to monitor the activity of the code you then press F5 or go to the run tab and choose the Start Debugging option then press Launch and breakpoint controls will appear, and the code will stop when it meets the breakpoint.

![https://www.linkedin.com/in/nqubeko-gcabashe/](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8azrav7surlxsxv6zj3x.png)
> this image shows what you will see when you running your project on debug mode and your code has hit the breakpoint on visual Studio Code.
![https://www.linkedin.com/in/nqubeko-gcabashe/](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ssfon04taeepky3wyesf.jpg)
> this image shows the same thing just in the chrome browser, things stop when the project is stuck on your breakpoint.

![https://www.linkedin.com/in/nqubeko-gcabashe/](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/udi4iug2i4mzl5cfhmim.jpg)

> Here we can see chrome representation of the same thing from VS Code with data showing on the side and also the breakpoint hung on the JS.

These are mostly for when you dealing with objects and also intend to see the values in the variables of your javascript code during run time, you can definitely use it with your typescript code also.

Please tell me how I can grow my debugging toolbox!! 

