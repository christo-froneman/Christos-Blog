---
title: Angular - A simple Angular Frontend App for our API
author: "@christo"
dates:
  published: "2023-07-31"
description: This is a simple Angular frontend app to interface with our Web API
---

# A simple Angular App for our Web API

## TL;DR
Before I fall asleep, fall over and crack my head open, can you please get to the point?

- The source code for this app can be found on my <a href="https://github.com/christo-froneman/BPM-Angular" target="_blank">Github Repository</a>
- This app is hosted on Render: <a href="https://beta-product-management.onrender.com" target="_blank">Beta Product Management Angular</a>

## What is this app?
This is a rinse and repeat of the Vue app covered in the previous blog, except it focuses on Angular.

Why did I write it?
- I have been out of the developement game for a while now (wow, has it really been almost 2 years?), doing some DevOps work for PwC (don't judge me too harshly, the money is studentdous, OK?).  But I'm not kidding anybody.  I am a developer at heart and I want to get back into it.  To refamiliarize myself with the basics of Angular, I followed Deborah Kurata's excellent Pluralsight course.
- I needed a frontend app to interface with our nifty little minimal ASP.NET Core Web API app.  So while I followed along with the course, I adapted the app to call out Web API that we devloped earlier instead of using hard coded JSON data.

### Refreshing Angular Basics
This Angular app has many flaws, and that is fine since the primary goal for writing it was to resfresh some of the core principles of Angular, and it did a fine job doing that:
- Using the Angular CLI to create the app
- Using CLI / Webpack to build the app
- Bindings
- Components
- Services
- Routing
- Using http to do API calls
- How to host the app on <a href="https://render.com" target="_blank">Render</a> and set up CI/CD

### Interface with our Web API
- I only implemented 2 API calls
  - getProducts
  - getProduct:id
- When I have more time, I plan to expand this app and implement the other CRUD components