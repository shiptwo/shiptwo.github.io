---
layout: post
title:  "Higher Order Functions"
author: nilesh
categories: [ JavaScript, Functional Programming ]
image: "https://images.unsplash.com/photo-1515472297483-9d89d39c85e8?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1079&q=80"
comments: false
courtesy: '<span>Photo by <a href="https://unsplash.com/@twinsfisch?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Isabella and Louisa Fischer</a> on <a href="https://unsplash.com/s/photos/wrapper?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>'
read_time: 5
---
Higher Order Function is a **Functional Programming** concept which is very helful in terms of **reusability** & **readability**.

## :zzz: TL;DR
Higher Order Functions are simply functions that take other functions as arguments or return a function as result.
A quote from [**Wikipedia**](https://en.wikipedia.org/wiki/Higher-order_function)
> A higher-order function is a function that does at least one of the following:
- takes one or more functions as arguments (i.e. procedural parameters),
- returns a function as its result.

## :pizza: Our piece
Now what it means is that, the Higher Order Function is going to provide us **some additional functionality around our own function** that we pass to it.

**Wrapper** is how I make out it & remember.
> Wrapper: One who, or that which, wraps.

The most common example we see with JavaScript is the Array `map` [function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map). 

It takes a function that is run on each element of the array to return a new array. Let's break it down:
- It iterates on each element of array
- It executes the function passed on argument on each element
- It returns a new array

## :computer: Some actuals

Consider an example, we have an array of numbers & we want to multiply each element by 2 (square function in Maths).
```javascript
// create array of numbers
const numbers = [ 2, 3, 4, 5 ];
// Function that takes a number & 
// returns result that is the product of number with itself (square)
const square = (num) => num * num;
// new array created using map function, 
// that uses square function on each element in numbers array
const squared_numbers = numbers.map(aNumber => square(aNumber));
// printing the input & output arrays
console.log('Numbers: ', numbers);
console.log('Squared Numbers: ', squared_numbers);
```
Here is the output when we run it in browser console:

![image]({{ site.baseurl }}/assets/images/hof-output.png)

Some few more examples of Higher Order Functions too that we use daily but fail to notice them:
- filter
- reduce
- some

Similar concept is leveraged by **React** for **Higher Order Components** which I will cover in another article.