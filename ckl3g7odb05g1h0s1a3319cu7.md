## Quick dive into CSS Preprocessors

In this article, you would learn about CSS preprocessors, and by the end of your reading, you would be on your way to adding one of them to your portfolio.


### Prerequisites?
Before we even discuss CSS preprocessors, you should know what CSS is, if you don't, you should probably learn it after now so you can follow up with this tutorial. 
#### What do you need to know to get started:

- Good knowledge of CSS

- Code editor

- Command-line


## What are CSS preprocessors?

According to  [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Glossary/CSS_preprocessor), A CSS preprocessor is a program that lets you generate CSS from the preprocessor's own unique syntax. CSS preprocessors extend the default functionality of CSS and enable you to use logic in your CSS code, such as variables, nesting, inheritance, mixins, functions, and mathematical operations. 

Since the browser cannot understand the syntax of preprocessors, It compiles into Vanilla CSS that the browser can work with. CSS preprocessors make it easy to create CSS.


## Why you should use CSS Preprocessors?

- They make the CSS structure more readable and easier to maintain.

- They reduce development time.

- They add logic and other functionalities to CSS.

- Unlimited reusability (Obeys the DRY rule).

- Flexibility

> DRY rule says "Don't Repeat Yourself"

## Different types of CSS Preprocessors

###  [SASS](https://sass-lang.com/) 

![1_Fk9lVjzWan0OgYa828emhw.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1612608642753/5hIiBcKIg.png)

Sass is the acronym for “Syntactically Awesome Style Sheets” and is the oldest CSS preprocessor, released in 2006. It is one of the most widely used CSS Preprocessors. It has various features to help developers write better and cleaner CSS code. Sass is written in Ruby.

#### SASS VS SCSS
They are actually both Sass with a different syntax. SCSS is basically a newer version, Sass Version 3.

SCSS (Sassy CSS) has a CSS-like syntax, which is much easier to read. It is an extension of CSS, whereas Sass has a more different syntax. Their file extension is also different: .sass & .scss .

![1_Cj_8NyQphUuRdE8zZfMt6g.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1612608686107/rbKVXHPBx.png)

###  [LESS](http://lesscss.org/) 

![index-of-images-partner-logos-less-png-300_170.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1612608829780/Mw5AZtFob.png)

LESS is an acronym for “Leaner Stylesheets”. It was released three years after Sass, in 2009. The LESS CSS preprocessor is, in fact, a JavaScript library that extends the default functionalities of CSS. As it’s written in JavaScript, we need Node.js to install and run the LESS compiler. However, we can also compile LESS on the fly by adding .less files and the LESS converter to the <head> section of our HTML page. LESS is the strongest competitor to Sass and has the second-largest user base.


###  [STYLUS](https://stylus-lang.com/) 

![stylus.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1612608852085/66dgevVNe.png)

Stylus is written in Node.js and fits perfectly with the JavaScript stack so that developers can easily integrate it into their Node projects. It was influenced by both Sass and LESS. Stylus combines the powerful logical abilities of Sass with the easy and straightforward setup of LESS. Stylus offers a great deal of flexibility in writing syntax, supports native CSS as well as allows omission of brackets colons, and semicolons.


## Cool Features of CSS Preprocessors

### Variable: 
Like in other programming languages, we can use variables to store values and reuse them later. Variable are great because they allow you to store values that can be reused several times over.
For example, you are working on a web page with different sections with the same background color, rather than styling with these colors over and over again, you can simply store the color in a variable and call it where ever you need it, with this, you can easily change the color once without going over the whole codebase. Little effort, great changes!

```
//Defining a variable
$bg-color: red;

//Using a variable
header{
background-color: $bg-color;
}

footer{
background-color: $bg-color;
}

``` 

### Mixins
Mixins are similar to a function and can be used to group CSS declarations together. They are reusable like variables and are a great way to reduce code redundancy. You can use them in any class with @import.


```
$font-size: 18px;

//Creating a mixin
@mixin main-font ($font-size) {
font-family: Roboto;
font-style: 500px;
font-size: $font-size;
font-color: blue;
}

//Using the mixin
header {
 @include main-font
}

``` 
Using main-font anywhere saves from writing those 4 lines of code repeatedly. Awesome right?

### Nesting
While HTML supports nesting, standard CSS does not. CSS preprocessors allow you to nest child selectors inside their parent selector and this means

Rather than do this:

```
footer ul {
    list-style: none;
}
footer  a {
    display: block;
	text-decoration: none;
	padding: 0.5rem;
}
footer  a:hover {
    text-decoration: underline;
}
``` 

Nesting allows you to store all style rules belonging to the same parent or grandparent right under each other.

```
footer {
	ul {
		list-style: none;
	}
	a {
		display: block;
		text-decoration: none;
		padding: 0.5rem;
		:hover {
			text-decoration: underline;
		}
	}
}
``` 
This allows you to write better-structured code, reduce code redundancy and improve readability.

### Import
Import helps you organize and modularize your stylesheets. This means that you will be able to split your huge style.css file into several smaller files that will be easier to maintain, understand, and organize.

Although standard CSS now has the @import feature, it works differently in CSS preprocessor. While CSS sends an HTTP request to the server each time to import a file, CSS preprocessor like Sass does it without an HTTP request, which is a faster approach and means only one HTTP request.

```
@import 'cart'
@import 'checkout'
@import 'buttons'
@import 'font'

``` 

### Mathematical Operation
You can use mathematical operations like addition (+), subtraction (-), multiplication (*), and division (/).

```

$nav-height: 50px;

body {
	padding-top: $nav-height + 30px;
}

.nav {
	position: fixed;
	top: 0;
	width: 100%;
	height: $nav-height;
}

``` 

### Extend
The @extend rule lets you share properties from one selector to another. It brings inheritance right into your stylesheet. Instead of outputting multiple declarations, they output a list of classes without repeating your properties. This way you can avoid repetition of code in your output as well.

```
.box {
  margin: 1em;
  padding: 1em;  
  border: 2px solid red;
}

.box-blue {
  @extend .box;
  border-color: blue;
}

.box-red {
  @extend .box;
  border-color: red;
}

``` 


## Things to consider before choosing one:

- Ensure it fits your workflow


- Compatibility with existing code


- Available features(Compare all depending on your need)


- Community


- Which feels better to you???

Note: They all have about the same functionalities


## Conclusion: 

There are a lot of pros to using CSS Preprocessors and you should consider using one in your next project. Your choice of CSS Preprocessors largely depends on your preference and project requirements. They are pretty much the same and are easy to learn, you just need to pick one, take the time to practice it, and use it to its full potential.

Till I come your way again, Adios!










