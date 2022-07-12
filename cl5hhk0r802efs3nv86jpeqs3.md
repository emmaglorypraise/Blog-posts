## Setting up Tailwind in your React Project

Setting up Tailwind in your React Project
When you don't sure what to do, I think starting a project can be one of the hardest parts, but other times it can also be the easiest.

This tutorial will demonstrate how to quickly (depending on the speed of your system😂) set up your react project with TailwindCSS.

Follow this guide step by step:


- Create your react project
 
```
npx create-react-app my-project-name

```
When you see happy hacking! you have successfully installed it.

![](https://paper-attachments.dropbox.com/s_BC9DF656DAB335173FABFF5AB49D4240E3C1252C29496AEFFAD6193F9853D878_1657584807537_3.png)


Navigate into the new directory created by:

```
    cd my-project-name

```

- Install tailwind and its peer dependency via NPM or Yarn 

```    
npm install -D tailwindcss postcss autoprefixer

```

- To  generate both `tailwind.config.js` and `postcss.config.js`, run the init command.

```    
npx tailwindcss init -p
```

You are almost done with the installation, now open your code editor by running

```
    code .
```

- Add the paths of all your template files in your tailwind.config file

``` 
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

- Add the Tailwind directives to your CSS

Add the `@tailwind` directives for each of Tailwind’s layers to your `./src/index.css` file.

```
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
```

- Start your build process with 

```
    npm run start or npm start

```
![](https://paper-attachments.dropbox.com/s_BC9DF656DAB335173FABFF5AB49D4240E3C1252C29496AEFFAD6193F9853D878_1657585126009_NivXNCFe.png)




- Start using Tailwind in your project

Start using Tailwind’s utility classes to style your content. To test if Tailwind is installed properly, delete the code inside of App.js, and paste this:

```
    <div>
            <h1 className='text-bold text-[45px] text-red-700'>
              Hiiii, Just testing if Tailwind works
            </h1>
    </div>
```

![](https://paper-attachments.dropbox.com/s_BC9DF656DAB335173FABFF5AB49D4240E3C1252C29496AEFFAD6193F9853D878_1657585291134_4.png)


You should see this below on your browser.

![](https://paper-attachments.dropbox.com/s_BC9DF656DAB335173FABFF5AB49D4240E3C1252C29496AEFFAD6193F9853D878_1657585352811_6.png)


Hurray! you have successfully installed tailwind in your react project.

Happy coding!

Learn how to setup tailwind CSS in your Vue project in my previous article [here](https://glorypraise.hashnode.dev/setting-up-tailwind-css-in-your-vue-project).

Till next time, 

Adios!
