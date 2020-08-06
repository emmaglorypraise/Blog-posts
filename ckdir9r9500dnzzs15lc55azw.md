## Understanding Max-Width and Min-Width in CSS Media Query

# What is a Media Query? 

Media query is used to apply specified CSS, depending on the device and whether it matches the media query criteria. This is useful when making a web page responsive because you can apply a particular style to a particular device size so the web page looks good across several devices.

There is much more to media query but this article is focused on explaining the differences between the two terms.


# Min-Width:

This is used to set a particular style when the width of a device is greater or equal to the set width.

For example:

```
@media (min-width: 600px)  {
background-color: blue;
}

``` 

This query tells your browser to apply this style if the device has a width that is greater than or equal to 600px. This means if the device has a width of 600px or more, the background colour will be blue.


# Max-Width:

This is used to set a particular style when the width of a device is less than or equal to the set width.

For example:

```
@media (max-width: 600px)  {
background-color: green;
}

``` 

This query tells your browser to apply this style if the device is less than or equal to 600px. This means for every device with a width of 600px and less, the background colour will be green.

So simply put, min-width is for greater and equal to the set width while max-width is for less than or equal to the set width.


> Min-width >= set width

> Max-width <= set width

Media query seems very confusing at first and I hope this explanation helps you remember the difference between Min-width and Max-width when writing media queries in CSS. 

Don't forget!