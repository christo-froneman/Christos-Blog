---
title: "ASP.NET Core Web API"
author: "@christo"
dates:
  published: "2023-07-23"
description: How to build a minimal Web API using Entity Framework Core and SQLite
---

# ASP.NET Core Minimal Web API

## TL;DR
Can you please just cut to the chase already?  Sure I can.

- The source code for this app can be found on my <a href="https://github.com/christo-froneman/BetaHardwareAPI" target="_blank">Github Repository</a>.
- This app is hosted in Microsoft Azure.  To use the app without a frontend, pull up it's <a href="https://betahardwareapi.azurewebsites.net/swagger/index.html" target="_blank">Swagger Page</a> which documents the API and allows you to test all methods.
- The <a href="https://learn.microsoft.com/en-us/training/modules/build-web-api-minimal-database/1-introduction" target="_blank">Microsoft Documentation</a> contains detailed instructions on how to set this up from scratch.

## Introduction
When you build a web application that deals with data, you'll most likely want to store that data in a database. Fortunately, minimal APIs built on ASP.NET Core can be easily integrated with a large variety of databases by using Entity Framework (EF) Core.

## Scenario
You're a developer on a team. You've built an API that handles create, read, update, and delete (CRUD) operations on a table of data. You plan to build a front-end application that uses that API. You want to store the data in a database so that you can use the data in your front-end application.

## What does this app demonstrate?
How to use EF Core to persist your data and query your database using SQLite.

## Bruh, did you really do this on a Mac?
Aw, well thanks for asking mate.  Yes, yes I did.  I took full advantage of the recent Amazon Prime day and scored a great deal on a Macbook Air 15 inch screen.  This is my first Mac and all I have to say is: why didn't you convince me to do this sooner?  This thing **rocks**!!

With Microsoft's stuff becoming more and more cross platform oriented, I had no trouble setting up a full development environment, including .NET and Visual Studio.  Neat, huh?  But to be honest, the C# Dev Kit suite of extensions for VS Code knocks it out of the park.  As a frontend developer I already love VS Code, but these extensions make for a pretty good .NET / C# development experience using Code.

## Where's the Frontend Apps?
I also have two simple frontend apps that interface with this API - one is written in Vue and the other in Angular.  I have separate blog posts to cover these frontend apps.