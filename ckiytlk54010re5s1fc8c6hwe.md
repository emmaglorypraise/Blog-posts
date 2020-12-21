## Getting Started with APIs in JavaScript

<span class="s"></span>

# Getting Started with APIs in JavaScript


<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/4480/1*kI_kJvy7f7TRLhP0tJ_2QQ.png" width="2240" height="1260" srcSet="https://miro.medium.com/max/552/1*kI_kJvy7f7TRLhP0tJ_2QQ.png 276w, https://miro.medium.com/max/1104/1*kI_kJvy7f7TRLhP0tJ_2QQ.png 552w, https://miro.medium.com/max/1280/1*kI_kJvy7f7TRLhP0tJ_2QQ.png 640w, https://miro.medium.com/max/1400/1*kI_kJvy7f7TRLhP0tJ_2QQ.png 700w" sizes="700px"/></noscript>

# **What is an API?**

API is the acronym for Application Programming Interface. Like the name implies it serves as an intermediary that allows interaction and communication between software products.

So with APIs, you can integrate features, products, and services from already existing ones into your application without building them yourself.

# Why you should use an API?

1.  It helps you get access to large data: With APIs, you don’t have to hard code data into your web application, you can just connect to an API and get real-time data or dummy data as the case might be. For example, you can build a weather app that tells the weather condition of a place without knowing the actual weather condition yourself.
2.  It helps you integrate cool stuffs to your website: You can integrate cool stuff easily like payment gateways, google maps, authentication channels from popular sources like Google or Facebook, services from eateries, agriculture, health, movies, etc
3.  APIs are great time savers: APIs allow developers to save time by taking advantage of a platform’s implementation to do the nitty-gritty work. This helps reduce the amount of code developers need to write and also helps create more consistency across apps for the same platform.

![Image for post](https://miro.medium.com/max/60/1*biLs0r8qLhaaorteiG6Dxg.jpeg?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/12000/1*biLs0r8qLhaaorteiG6Dxg.jpeg" width="6000" height="4000" srcSet="https://miro.medium.com/max/552/1*biLs0r8qLhaaorteiG6Dxg.jpeg 276w, https://miro.medium.com/max/1104/1*biLs0r8qLhaaorteiG6Dxg.jpeg 552w, https://miro.medium.com/max/1280/1*biLs0r8qLhaaorteiG6Dxg.jpeg 640w, https://miro.medium.com/max/1400/1*biLs0r8qLhaaorteiG6Dxg.jpeg 700w" sizes="700px"/></noscript>

Photo by [Nathan da Silva](https://unsplash.com/@silvawebdesigns?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/javascript?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

# Getting Started???

Firstly, you need to know what kind of API you need, what kind of application are you trying to build or what feature do you need from the API?

When you have settled tha<span id="rmm"><span id="rmm">t</span></span>, you can then proceed to find an API to suit your need. While there are free APIs available, you might need to pay to be able to use some, you can find free APIs [here](https://github.com/public-apis/public-apis) and [here](https://apilist.fun/).

After settling for which API to use, go to the APIs documentation or website on how to use it.

In this article, I am going to be creating a web page that displays pictures of cute dogs(I don’t like dogs tho).

Here is the link to the documentation we’ll be using: [Link](https://dog.ceo/dog-api/)

![Image for post](https://miro.medium.com/max/60/1*OnsSrGjdLNswEtSBhpkONg.png?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/2732/1*OnsSrGjdLNswEtSBhpkONg.png" width="1366" height="658" srcSet="https://miro.medium.com/max/552/1*OnsSrGjdLNswEtSBhpkONg.png 276w, https://miro.medium.com/max/1104/1*OnsSrGjdLNswEtSBhpkONg.png 552w, https://miro.medium.com/max/1280/1*OnsSrGjdLNswEtSBhpkONg.png 640w, https://miro.medium.com/max/1400/1*OnsSrGjdLNswEtSBhpkONg.png 700w" sizes="700px"/></noscript>

Home page of API documentation

# Reading the API Documentation for information:

Before you start using an API, you should first read their documentation to know how to use their API because although all API basically work through the request and response method, they might just have different methods of doing that.

Most of the time, the documentation will include examples that you can tweak to get the output that you’re after.

Some APIs require you to sign up before using them mostly for authentication purposes and to track your requests. After signing up and confirming your email and then you can now locate your dashboard for your API key.

But in this case, we don’t need to sign up, we can just use the API straight away.

# Getting an API key

An API key is a unique identifier or code that is used to authenticate and connect to an API. It is mostly used to track your requests. Now the API key may not necessarily be to track the user as you can have more than one API key, rather it is used to identify the application or program that is calling an API.

Note that not all API requests for an API key, also your API keys is like a password that shouldn’t be shared with other people.

Like I mentioned earlier, we don’t need an API key for this article, just have that in mind for subsequent APIs you would be using.

# Fetching/Requesting data from the API:

To start, you would need to create an HTML, CSS, and Javascript file so you can practice along.

Here is my HTML file, we would be using JavaScript to generate data from the API :

![Image for post](https://miro.medium.com/max/60/1*DLGwqt2R_aqtJsDsPdACyQ.png?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/3028/1*DLGwqt2R_aqtJsDsPdACyQ.png" width="1514" height="912" srcSet="https://miro.medium.com/max/552/1*DLGwqt2R_aqtJsDsPdACyQ.png 276w, https://miro.medium.com/max/1104/1*DLGwqt2R_aqtJsDsPdACyQ.png 552w, https://miro.medium.com/max/1280/1*DLGwqt2R_aqtJsDsPdACyQ.png 640w, https://miro.medium.com/max/1400/1*DLGwqt2R_aqtJsDsPdACyQ.png 700w" sizes="700px"/></noscript>

HTML file

Since APIs work through a request and response method. You need to send a request using **HTTPS** and **fetch()**. This has become the standard way of calling APIs in JavaScript.

The **fetch()** method allows us to perform HTTP requests to a server. If we want to access the data, we require two **.then()** handlers. We first define the path (fetch), request data from the server (request), and define the content type(body) using the **.then** handler(call back), then finally access the data (response) using the **.then()** handler.

Here’s what I mean:

![Image for post](https://miro.medium.com/max/60/1*6ljDJXcsiCFPJafVFuhkmQ.png?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/2892/1*6ljDJXcsiCFPJafVFuhkmQ.png" width="1446" height="516" srcSet="https://miro.medium.com/max/552/1*6ljDJXcsiCFPJafVFuhkmQ.png 276w, https://miro.medium.com/max/1104/1*6ljDJXcsiCFPJafVFuhkmQ.png 552w, https://miro.medium.com/max/1280/1*6ljDJXcsiCFPJafVFuhkmQ.png 640w, https://miro.medium.com/max/1400/1*6ljDJXcsiCFPJafVFuhkmQ.png 700w" sizes="700px"/></noscript>

Applying the same method, we do this:

![Image for post](https://miro.medium.com/max/60/1*IZAZ_S2dQFMg_hCUN1Aeeg.png?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/2588/1*IZAZ_S2dQFMg_hCUN1Aeeg.png" width="1294" height="516" srcSet="https://miro.medium.com/max/552/1*IZAZ_S2dQFMg_hCUN1Aeeg.png 276w, https://miro.medium.com/max/1104/1*IZAZ_S2dQFMg_hCUN1Aeeg.png 552w, https://miro.medium.com/max/1280/1*IZAZ_S2dQFMg_hCUN1Aeeg.png 640w, https://miro.medium.com/max/1400/1*IZAZ_S2dQFMg_hCUN1Aeeg.png 700w" sizes="700px"/></noscript>

We can check the console in the Developer tool of the browser to see if it works

![Image for post](https://miro.medium.com/max/60/1*oUFDsbnG2QcmGtx3CR2i4w.png?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/2732/1*oUFDsbnG2QcmGtx3CR2i4w.png" width="1366" height="631" srcSet="https://miro.medium.com/max/552/1*oUFDsbnG2QcmGtx3CR2i4w.png 276w, https://miro.medium.com/max/1104/1*oUFDsbnG2QcmGtx3CR2i4w.png 552w, https://miro.medium.com/max/1280/1*oUFDsbnG2QcmGtx3CR2i4w.png 640w, https://miro.medium.com/max/1400/1*oUFDsbnG2QcmGtx3CR2i4w.png 700w" sizes="700px"/></noscript>

# Displaying data on the browser

Now that we have successfully retrieved data from the API, we have to now display it on the browser using the DOM. The DOM allows JavaScript to communicate with HTML. If you are not familiar with using the DOM, read this [guide](https://www.w3schools.com/js/js_htmldom.asp).

We’ll change that console.log to a function so we can use the data easily without running into any access errors. We will create an arrow function and use data as its parameter. Every other code henceforth should be written inside this function.

![Image for post](https://miro.medium.com/max/60/1*s_LkeYTOsO9C7bpK8K-TVQ.png?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/2588/1*s_LkeYTOsO9C7bpK8K-TVQ.png" width="1294" height="732" srcSet="https://miro.medium.com/max/552/1*s_LkeYTOsO9C7bpK8K-TVQ.png 276w, https://miro.medium.com/max/1104/1*s_LkeYTOsO9C7bpK8K-TVQ.png 552w, https://miro.medium.com/max/1280/1*s_LkeYTOsO9C7bpK8K-TVQ.png 640w, https://miro.medium.com/max/1400/1*s_LkeYTOsO9C7bpK8K-TVQ.png 700w" sizes="700px"/></noscript>

Since we just have one root element in the HTML file which is the **.app** div. We’ll access it using **querySelector()**.

![Image for post](https://miro.medium.com/max/60/1*Aum0LQtPR7d_y7AEXVxEnw.png?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/2220/1*Aum0LQtPR7d_y7AEXVxEnw.png" width="1110" height="480" srcSet="https://miro.medium.com/max/552/1*Aum0LQtPR7d_y7AEXVxEnw.png 276w, https://miro.medium.com/max/1104/1*Aum0LQtPR7d_y7AEXVxEnw.png 552w, https://miro.medium.com/max/1280/1*Aum0LQtPR7d_y7AEXVxEnw.png 640w, https://miro.medium.com/max/1400/1*Aum0LQtPR7d_y7AEXVxEnw.png 700w" sizes="700px"/></noscript>

We would then use **forEach()** to display the pictures from the array of images, we want each image to be in a div and they should all be in the **.app** div.

Using **createElements()** We can create a div and give it a class name of **card** using **className**. Here is the code:

![Image for post](https://miro.medium.com/max/60/1*wHLYSKw28VC-9oRsJVRVYw.png?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/2252/1*wHLYSKw28VC-9oRsJVRVYw.png" width="1126" height="660" srcSet="https://miro.medium.com/max/552/1*wHLYSKw28VC-9oRsJVRVYw.png 276w, https://miro.medium.com/max/1104/1*wHLYSKw28VC-9oRsJVRVYw.png 552w, https://miro.medium.com/max/1280/1*wHLYSKw28VC-9oRsJVRVYw.png 640w, https://miro.medium.com/max/1400/1*wHLYSKw28VC-9oRsJVRVYw.png 700w" sizes="700px"/></noscript>

We would repeat the same steps to create an image element and set the source to the image URL from the API. I used a template string to avoid repeating the same code multiple times.

![Image for post](https://miro.medium.com/max/60/1*c76-uvbc_aFFzEf__xOALQ.png?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/2320/1*c76-uvbc_aFFzEf__xOALQ.png" width="1160" height="768" srcSet="https://miro.medium.com/max/552/1*c76-uvbc_aFFzEf__xOALQ.png 276w, https://miro.medium.com/max/1104/1*c76-uvbc_aFFzEf__xOALQ.png 552w, https://miro.medium.com/max/1280/1*c76-uvbc_aFFzEf__xOALQ.png 640w, https://miro.medium.com/max/1400/1*c76-uvbc_aFFzEf__xOALQ.png 700w" sizes="700px"/></noscript>

Okay great, we are done with that but this is only visible in the console, to make it show in the browser, we’ll append it to the **.app** div already in the HTML file using **appendChild()**. We’ll append the **card** div to the **.app** div and then the image to the **.card** div. Here's the code:

![Image for post](https://miro.medium.com/max/60/1*DkNmSgHyz4CUWCDNJOzUhw.png?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/2692/1*DkNmSgHyz4CUWCDNJOzUhw.png" width="1346" height="480" srcSet="https://miro.medium.com/max/552/1*DkNmSgHyz4CUWCDNJOzUhw.png 276w, https://miro.medium.com/max/1104/1*DkNmSgHyz4CUWCDNJOzUhw.png 552w, https://miro.medium.com/max/1280/1*DkNmSgHyz4CUWCDNJOzUhw.png 640w, https://miro.medium.com/max/1400/1*DkNmSgHyz4CUWCDNJOzUhw.png 700w" sizes="700px"/></noscript>

So far, this is what the code looks like:

![Image for post](https://miro.medium.com/max/56/1*CyBAgUfe4dSOg35wDWRehA.png?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/2892/1*CyBAgUfe4dSOg35wDWRehA.png" width="1446" height="1524" srcSet="https://miro.medium.com/max/552/1*CyBAgUfe4dSOg35wDWRehA.png 276w, https://miro.medium.com/max/1104/1*CyBAgUfe4dSOg35wDWRehA.png 552w, https://miro.medium.com/max/1280/1*CyBAgUfe4dSOg35wDWRehA.png 640w, https://miro.medium.com/max/1400/1*CyBAgUfe4dSOg35wDWRehA.png 700w" sizes="700px"/></noscript>

And Viola! we are done.

To make it look better, let's add some CSS:

![Image for post](https://miro.medium.com/max/36/1*Rk9C9hMglCwQlcphFKovnA.png?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/1476/1*Rk9C9hMglCwQlcphFKovnA.png" width="738" height="1236" srcSet="https://miro.medium.com/max/552/1*Rk9C9hMglCwQlcphFKovnA.png 276w, https://miro.medium.com/max/1104/1*Rk9C9hMglCwQlcphFKovnA.png 552w, https://miro.medium.com/max/1280/1*Rk9C9hMglCwQlcphFKovnA.png 640w, https://miro.medium.com/max/1400/1*Rk9C9hMglCwQlcphFKovnA.png 700w" sizes="700px"/></noscript>

So here, you have been able to connect to an API and display the images from the API on the browser using DOM.

![Image for post](https://miro.medium.com/max/60/1*kX5qff3bDUnvYNGt5hhRWg.png?q=20)

<noscript><img alt="Image for post" class="fp fe fa hx x" src="https://miro.medium.com/max/2732/1*kX5qff3bDUnvYNGt5hhRWg.png" width="1366" height="661" srcSet="https://miro.medium.com/max/552/1*kX5qff3bDUnvYNGt5hhRWg.png 276w, https://miro.medium.com/max/1104/1*kX5qff3bDUnvYNGt5hhRWg.png 552w, https://miro.medium.com/max/1280/1*kX5qff3bDUnvYNGt5hhRWg.png 640w, https://miro.medium.com/max/1400/1*kX5qff3bDUnvYNGt5hhRWg.png 700w" sizes="700px"/></noscript>