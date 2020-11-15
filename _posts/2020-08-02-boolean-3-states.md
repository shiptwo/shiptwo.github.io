---
layout: post
title:  "Boolean with 3 States"
author: nilesh
categories: [ Java ]
image: "https://images.unsplash.com/photo-1530051528223-01d6a86a154c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=960&h=500&q=80"
comments: false
courtesy: '<span>Photo by <a href="https://unsplash.com/@florenciaviadana?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Florencia Viadana</a> on <a href="https://unsplash.com/?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>'
read_time: 4
---
It's wonderful to know how we can use `wrappers` & `primitives` to our benefit. This was something I found while reading through Oracle Java Tutorials.

So without further due, here is the thing.

## Back to Basics
Boolean by definition has 2 states or 2 values. Here is a quote about it from [Wikipedia](https://en.wikipedia.org/wiki/Boolean_data_type):
> In computer science, the Boolean data type is a data type that has one of two possible values (usually denoted true and false) which is intended to represent the two truth values of logic and Boolean algebra.

But when Java introduced `wrapper` classes around `primitive` it essentially casted them into `objects`. Now since a default value for an `object` is `null`, these wrappers can also be `null` & so is `Boolean` with a big 'B'.
> Default value for an `object` is `null`, so `wrappers` can be `null` & so is `Boolean` with a big 'B'

## The trick
This way, we can a `Boolean` wrapper reference hold any of 3 states `null`, `true`, `false`. We could use `null` as a special condition if we require such.

## Some code
```java
// By default is set to null unless we do
private Boolean checked;

// By default boolean primitive will be set to false
private boolean confirmed;

// Returns null if 'checked' is not set
public Boolean isChecked() {
    return this.checked;
}

// Returns false as 'confirmed' was a primitive casted into wrapper
public Boolean isConfirmed() {
    return this.confirmed;
}
```

## Caveats
We should however use this whenever required & not everywhere & condsider these facts:
- Declaring it as a wrapper needs us an additional null check before comparing its truth values
- Ojects are larger in size compared to primitives

That's all I had for this post. Thank you.