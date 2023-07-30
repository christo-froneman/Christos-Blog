---
title: Vue - A simple Vue Frontend App for our API
author: "@christo"
dates:
  published: "2023-07-30"
description: This is a simple Vue frontend app to interface with our Web API
---

# A simple Vue Frontend App for our Web API

## TL;DR
Look man, I don't care about your ramblings, give me the MEAT and TATERS!

- The source code for this app can be found on my <a href="https://github.com/christo-froneman/BPM-Vue" target="_blank">Github Repository</a>
- This app is hosted on Render: <a href="https://bpm-vue.onrender.com/" target="_blank">Beta Product Management Vue</a>


## What is this app?
This is a super simple Vue frontend app that I wrote.

Why did I write it?
- I have primarily worked with Angular; never with Vue and wanted to learn the basics of the framework.
- I needed a frontend app to interface with our nifty little minimal ASP.NET Core Web API app.

### Learning Vue Basics
This Vue app is not a model of perfection by any means.  It only served to teach me some of the core principles of Vue:
- Using the Vue CLI to create the app
- Using CLI / Vite to build the app
- Composition API
- Bindings
- Single File Components
- Services
- Routing
- API calls with Axios
- How to host the app on <a href="https://render.com" target="_blank">Render</a> and set up CI/CD

### Interface with our Web API
- I only implemented 2 API calls
  - getProducts
  - getProduct:id
- When I have more time, I plan to expand this app and implement the other CRUD components