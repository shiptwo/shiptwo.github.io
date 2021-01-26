---
layout: post
title:  "Debugging in Spring Boot"
author: nilesh
categories: [ Spring Boot ]
image: "https://images.unsplash.com/photo-1463590469467-c60accd525f3?ixlib=rb-1.2.1&ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&auto=format&fit=crop&w=900&q=80"
comments: false
courtesy: '<span>Photo by <a href="https://unsplash.com/@samdasherx13?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Samuel Myles</a> on <a href="https://unsplash.com/s/photos/bug?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>'
read_time: 5
---
Spring Boot is an awesome way to build robust APIs fairly quickly. Its speed lies in the simplicity to run the apps like simple Java Programs. This article aims to help with debugging in Spring Boot Applications.

> **magic**, a quality of being beautiful and delightful in a way that seems remote from daily life.

For the sake of clarity, we will run the application via command line to understand better & avoid the IDE **magic** for the time.

# :star: Running Spring Boot application 
Usually we run Spring application using the Gradle Wrapper Script `gradlew` available in any Boot Application with `bootRun` task.
```bash
./gradlew bootRun
```

# :beetle: Debugging Spring Boot
You will find a lot of ways to debug Spring Boot Applications, here are the ones that I use often & find simple to use.


## :pushpin: Debug using --debug-jvm argument
- The first straight-forward way is to pass `--debug-jvm` flag while running `bootRun` task:
```bash
./gradlew bootRun --debug-jvm
```
- It will now print the port it is listening to & wait for you to connect your IDE to that port:
```bash
Listening for transport dt_socket at address: 5005
```
- Head over to your IDE & create a debug configuration to attach to that port. 
  - For Eclipse IDE open Debug Configurations, go to Menu -> Run -> Debug Configurations.
  - Double click Remote Java Application to create a new configuration.
  - Select a project for that configuration.
  - Connection Type should be Socket Attach.
  - Host will be localhost, port will be whatever that is printed while starting the application, i.e. 5005.
  - Click Apply & then Debug.
    ![image]({{ site.baseurl }}/assets/images/debug-conf-eclipse.png)  
- It is only after you connect, the Spring Boot application will start.   

## :pushpin: Debug using extended Gradle bootRun task
- In this option, you get to choose a debug port of yout choice.
- We will be extending the `bootRun` gradle task & provide JVM arguments to it.
- Edit your `build.gradle` & add below task:
  ```groovy
  bootRun {
	  jvmArgs=["-agentlib:jdwp=transport=dt_socket,server=y,suspend=y,address=14001"]
  }
  ```
- Set the `address` option to whichever port you need.
- Start your application with `bootRun` without any arguments:
  ```bash
  ./gradlew bootRun
  ```
- You can also let the application start up without waiting for an IDE to attach by setting the `suspend=n` in the arguments.
- Rest of the steps remain identical for creating & debug configuration & attaching the IDE to your Spring Boot Application.

Hope this information helped you in some way. Please feel free suggest any edits through issues in my git repository.