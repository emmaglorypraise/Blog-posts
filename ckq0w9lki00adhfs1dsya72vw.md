## Setting up Tailwind CSS in your Vue Project

## Outline
- Introduction to Tailwind CSS
- Why choose Tailwind CSS
- Creating your Vue project
- Installing Tailwind
- Create a configuration file
- Configure PostCSS
- Create a CSS file
- Import it to your Vue App
- Testing


![christopher-gower-m_HRfLhgABo-unsplash.jpg](Upload failed. Please re-upload the image)

## Introduction to Tailwind CSS

Tailwind CSS is a utility-first CSS framework which means it has various utility classes which help to create layouts and rapidly create custom designs. It is unlike the other common CSS frameworks like Bootstrap in the sense that Tailwind doesn’t provide any built-in UI components.

## Why choose Tailwind CSS

Tailwind has many advantages but the main benefit of Tailwind is that it relieves you from having to write loads of CSS, and you can instead use Tailwind directly in your HTML.  It makes the styling process much faster. You can create nice layouts in a much shorter time than doing it from scratch. It has other cool features like dark mode, a cool color palette, etc. Let’s see how we can use Tailwind CSS in a Vue project.


## Creating your Vue project

Create your Vue project by using:
    
```
vue create app-name
``` 
After that, redirect to your project folder and launch your vue app.


```
 cd app-name
 yarn serve or npm run dev
``` 
Tip: you can open your VS code editor from your terminal by:

```
code .
``` 
  
## Using Tailwind CDN

If you are working on a very small project, You can use Tailwind CSS by adding the CDN link to the HTML. 

```
 <link href="https://unpkg.com/tailwindcss@^2/dist/tailwind.min.css" rel="stylesheet">
``` 

Note: Please note that many of the features that make Tailwind CSS awesome are not available without incorporating Tailwind into your build process( and this is by installing Tailwind by NPM). Some limitations include:

- You can't customize Tailwind's default theme
- You can't install third-party plugins
- You can't use any directives like @apply, @variants, etc.

You can check the  [documentation](https://tailwindcss.com/docs/installation)  for more information.

## Installing Tailwind

Install Tailwind CSS using: 

```
npm install tailwindcss
# OR
yarn add tailwindcss
``` 
  
## Create a configuration file

To create a tailwind.js file in the root of your project, adding the basic Tailwind configuration. use the Tailwind command. 


```
./node_modules/.bin/tailwind init tailwind.js

``` 

## Configure PostCSS

Webpack (and Vue-loader which is a Webpack loader for Vue.js components) can be configured to use PostCSS which is a Webpack loader for CSS.

It will look for the configuration inside a `postcss.config.js` file and can build the app with CSS from the packages you added.

Create a `postcss.config.js`  in your project folder and configure it using this code


```
// postcss.config.js
    
const autoprefixer = require('autoprefixer');
const tailwindcss = require('tailwindcss');
    
module.exports = {
      plugins: [
        tailwindcss,
        autoprefixer,
      ],
};
``` 

## Create a CSS file

Now create a CSS file in your assets folder. You can put it inside a CSS or style folder for structure's sake. 

Now add this code, which adds the various packages of the Tailwind CSS library.

```
/* src/assets/style/index.css */
    
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
```  

Note: If you have lint errors, change it to:


```
    @import "tailwindcss/base";
    @import "tailwindcss/components";
    @import "tailwindcss/utilities";
``` 
  
## Import it to your Vue App

Edit the  src/main.js  file as shown here, adding an import line to include the new index.css stylesheet asset.


```

  import '@/assets/style/index.css'
``` 

## Testing 

To show it's working as expected, now you can use components straight from the Tailwind CSS component library. For example:
```
   <div class="text-red-600 bg-black">
         This is just a test
    </div>
```  

You can add the code above in your HelloWorld.vue file to see the result.

### Common error:
If you encounter a syntax error about  Tailwindcss requiring PostCSS 8, you can solve it by running these:
```
 npm uninstall tailwindcss postcss autoprefixer
 npm install tailwindcss@npm:@tailwindcss/postcss7-compat postcss@^7 autoprefixer@^9

``` 
   
This will uninstall and install the compatibility build. Read more  [here](https://github.com/postcss/postcss/wiki/PostCSS-8-for-end-users) .

I hope you find this article helpful.

Thanks for reading!
 