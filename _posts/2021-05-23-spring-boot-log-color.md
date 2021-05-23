---
layout: post
title:  "Log color in Spring Boot"
author: nilesh
categories: [ Spring Boot ]
image: "https://images.unsplash.com/photo-1607536242401-04b7b0e13330?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1276&q=80"
comments: false
courtesy: '<span>Photo by <a href="https://unsplash.com/@trfotos?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Toni  Reed</a> on <a href="https://unsplash.com/s/photos/crayon?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a></span>'
read_time: 3
---
  
Yes that's right! Staring at the bland plain logs is monotonous & cumbersome. It was & is painful to always figure out the warnings & errors out of logs.

![Plain Console]({{ site.baseurl }}/assets/images/std-color-console.png "Plain Console")

While in Oracle Commerce (ATG) we used to have a special program the `LogColorizer` to color the console output making it easy for us to figure out error (colored red) & warnings (colored yellow).

## :rainbow: Way to colors
Now with Spring I started missing it until I discovered that in their [documentation](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#features.logging.console-output.color-coded).  
Just follow these 2 steps:
- In your `application.properties` add below configuration:
    ```properties
    # default value is DETECT
    spring.output.ansi.enabled=ALWAYS
    ```
- In your terminal set the environment variable to enable ANSI output:
    ```shell
    export CLICOLOR=1
    ```
  
Now start you application to see the new look:  

![Colored Console]({{ site.baseurl }}/assets/images/ansi-color-console.png "Colored Console")

That's all. Thanks. Please feel free suggest me any edits or help you need.