---
title: "Getting started with React, JavaScript, and Tailwind: A step-by-step guide for new developers"
datePublished: Sun Mar 19 2023 22:38:35 GMT+0000 (Coordinated Universal Time)
cuid: clffzbw6w000409mphi6yeqk1
slug: getting-started-with-react-javascript-and-tailwind-a-step-by-step-guide-for-new-developers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1679265300079/cfc21a04-1df0-438b-8e8e-0e998966b4ab.png
tags: javascript, web-development, reactjs, tailwind-css

---

So I wanted to build a React project for the first time in a long time (1 month **😂**), and I wasn't sure how to start (I had forgotten the syntax, thanks to Next.js). I started to surf the internet, and I started writing this article as I built my project, only to check my blog before publishing and notice that I had already written an article on this topic last year [(read it here)](https://glorypraise.hashnode.dev/setting-up-tailwind-in-your-react-project). So take this as an update of that article or a more comprehensive guide (even though not much has changed).

### Introduction

React is a popular JavaScript library used for building user interfaces, while Tailwind is a CSS framework that makes styling web applications much easier. Creating a modern web application can seem daunting, especially if you're a new developer. But fear not! With the right tools and a bit of guidance, anyone can build a professional-looking web app.

If you're a new developer looking to create a project with React, JavaScript, and Tailwind, you've come to the right place. In this article, I'll guide you through the process of building a web application using React, JavaScript, and Tailwind. I added some JavaScript interactions to make it more helpful for beginners. So let's begin again 😊.

### Prerequisites

Before we start building our project, we need to have the following tools installed:

* Node.js
    
* NPM (Node Package Manager)
    
* Git(Optional but important)
    
* A text editor (e.g. Visual Studio Code)
    

### Step 1: Create a new React project

To create a new React project, we will use Create React App, which is a tool that helps developers set up a new React project with ease. Open a terminal window (which could be in your Visual Studio code editor) and run the following command:

```bash

npx create-react-app my-awesome-dapp
```

This command creates a new React project named `my-awesome-dapp`.

Once the project is created, navigate to the project directory:

```bash

cd my-awesome-dapp
```

### Step 2: Add Tailwind to the project

To add Tailwind to the project, we need to install the required dependencies. Run the following command in the terminal:

```plaintext

npm install -D tailwindcss postcss autoprefixer

```

This command installs Tailwind CSS, PostCSS, and Autoprefixer as development dependencies.

Next, we need to create the default Tailwind configuration files needed in the project folder. Run the following command in the terminal to create these files.

```bash

npx tailwindcss init -p
```

This command makes sure that not only are the files created but also that a default configuration structure is already available within these files.

This command creates a `tailwind.config.js` file in the project root directory.

Note: This file needs to be configured. Configure your template paths by adding the paths to all of your template files in your `tailwind.config.js` file. Replace the default code with the one below:

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./src/**/*.{js,jsx,ts,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

This command also creates a PostCSS configuration file named `postcss.config.js` in the project root directory and adds the following code to it. You don’t need to change this file.

```javascript

module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

Finally, we need to import the Tailwind CSS into our project. Open the `src/index.css` file and add the following code:

```css

@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Step 3: Create a sample component

Now that we have added Tailwind to our project, let's create a sample component. In the `src` directory, create a new file named `SampleComponent.js` and add the following code:

```javascript

import React from 'react';

const SampleComponent = () => {
  return (
    <div className="bg-gray-500 p-4">
      <h1 className="text-white text-2xl">Hello, World!</h1>
      <h3 className="text-white text-lg">I am a cool blockchain developer</h3>
    </div>
  );
};

export default SampleComponent;
```

This code creates a simple component with a gray background and white text.

### Step 4: Use JavaScript to add functionality:

```javascript

import React, { useState } from 'react';

const SampleComponent = () => {

// defines state variable 'color' and its updater function 'setColor' with initial value 'bg-gray-500'
  const [color, setColor] = useState('bg-gray-500');

// defines function 'changeColor' that sets the 'color' state variable to 'bg-blue-500'
  const changeColor = () => {
    setColor('bg-blue-500');
  };

  // renders a header and a button that calls the 'changeColor' function when clicked
  return (
    <div className={`${color} text-white p-4`}>
		      <h1 className=" text-2xl">Hello, World!</h1>
		      <h3 className=" text-lg">I am a cool blockchain developer</h3>
<button onClick={changeColor}>Change Color</button>
     </div>

  );
};

export default SampleComponent;
```

### Step 4: Use the sample component

To use the sample component, we need to import it into our `App.js` file. Open the `src/App.js` file and delete all the code in it, then add the following code:

```javascript

import React from 'react';
import SampleComponent from './SampleComponent';

function App() {
  return (
    <div className="App">
      <SampleComponent />
    </div>
  );
}

export default App;
```

This code imports the `SampleComponent` and uses it in the `App` component.

### Step 5: Start the development server

To view your project on the browser, start the development server by running the following command:

```bash

npm start
```

This will start the development server on [`http://localhost:3000`](http://localhost:3000).

### Step 6: Build the project for production

To build the project for production, run the following command in the terminal:

```bash

npm run build

```

This command builds the project for production and creates a `build` folder in the project root directory.

## Conclusion

In conclusion, we have learned how to create a project with React, JavaScript, and Tailwind step by step. We started by creating a new React project using Create React App and then added Tailwind to our project by installing its dependencies, creating its configuration files, and importing its CSS. We then created a sample component and used it in our `App.js` file. Finally, we built the project for production. With this knowledge, new developers can start building beautiful web applications using React, JavaScript, and Tailwind.

Till next time,

Adios!