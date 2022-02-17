---
layout: post
title: "Project: Inventory System"
date: 2022-02-17
categories: project
storage: inventoryImage.jpg
storeUp: /assets/img/Store.png
api: /assets/img/API.png
tags: Web-Development API React Flask Python
---

![Shelves with Boxes](/assets/img/inventoryImage.jpg)

## Live Demos

storeUp: https://apinventory.alectan.dev/storeup/
Backend/API: https://apinventory.alectan.dev/swagger/

## Setting the Scene
It’s been at least 5 years since I’ve joined the Tech ministry at my local church, and 1 year since I’ve started serving the ministry as one of its Tech Leads. As part of the Tech ministry, we provide technical support during church events and operations. This includes providing Live Audio Mixing, Lighting and Live Streaming Production, and managing internal software tooling such as Google Workspace. 

Naturally, this meant that the ministry would own a wide variety of resources. This ranges from small items like adaptors and cables, to large and expensive equipment such as our iMacs and Sound Desk. (If you must know we’re using the Behringer x32, very cool!).

Despite being responsible for such a large number of resources (some of which cost thousands of dollars), we’ve yet to establish a formal system to manage our inventory. Unsurprisingly, this led to various problems. 

We often have difficulty finding certain items within the building, let alone knowing what other items we currently own. Everyone simply had to remember what we have and where everything is.

Most of our resources are also used by multiple people throughout the week. This meant that some items may have been moved, or even damaged. The rest of the ministry are often notified of these changes through group messages, but such notices often get lost in the chat or just simply forgotten over time. This resulted in some items going missing, or broken items accidentally being used in a project.

When I was offered the position of Tech Lead, I was eager to start designing and implementing ways to manage our resources better. In collaboration with the other tech leads, we started off by reorganising our allocated building spaces. We designated each location to store certains types of items in storage boxes - with both items and storage boxes labelled for easy identification!

Despite the changes we’ve made we still needed something to track our inventory. We needed a system that can keep a record of where items are located, their current state, and any notes about the item that we want to remember. 

Enter [StoreUp](https://apinventory.alectan.dev/storeup/) and [APInventory](https://apinventory.alectan.dev/swagger/)!

## A Solution to the Problem

To provide the ministry the functionality that it needs, I’ve developed two applications - APInventory and StoreUP.

### APInventory

<figure>
    <img src="{{page.api}}" alt="logo">
</figure>

APInventory is a RESTful API built with Flask. It allows users to:
    - know what storages they have in their inventory, what they contain and where can be found.
    - Know the state of each item and where they ought to be stored.
    - Keep track of any notes regarding certain storage boxes, and items.

In addition to Flask, it uses extensions such as [Flask-Cors](https://flask-cors.readthedocs.io/en/latest/) to enable Cross-Origin-Resource-Sharing (CORS), and [Flask-SQLAlchemy](https://flask-sqlalchemy.palletsprojects.com/en/2.x/) for accessing databases using an ORM (SQLAlchemy). The API currently uses SQLite as its database for the demo.

Resource representations follow the [Collection+JSON](https://github.com/collection-json/spec) format due to its hypermedia capabilities. Its format also fits in with the semantics of the API resource - an inventory is a collection of storages, and a storage is a collection of items.

Users interact with the API by making the appropriate request (GET, POST, PUT, DELETE)  to the URLs provided by the collection resource. This is different to RPC style APIs where users are expected to know what endpoints to call, how to call them, and in what order. 

Instead each resource sent by the API includes several links which represent the actions that the client can make next. This means that the only endpoint clients are coupled to is the root endpoint (/). The rest are provided by the resource representation sent by the API. What these actions are specifically are conveyed by the format’s semantics, which are defined in its standard [here](https://github.com/collection-json/spec).

### storeUp

<figure>
    <img src="{{page.storeUp}}" alt="logo">
</figure>


StoreUP is a single-page client application for APInventory that I’ve built using React. 

Its components and icons are provided by [React-Bootstrap](https://react-bootstrap.github.io/) and [Bootstrap Icons](https://icons.getbootstrap.com/).
API calls are made using fetch, with application state and side effects managed by React Hooks.

## Lessons Learned
Here are a few of my highlights!

### My First React App

Prior to developing storeUp, I’ve never tried building an app with React before.

Back then I’ve only used HTML, CSS, Javascript, Bootstrap, and Jinja2 (Flask’s templating engine) to create any frontend I needed. While it's certainly possible to create storeUp without React, I’ve been wanting to learn React for some time already.

So I bought a copy of [Fullstack React](https://www.newline.co/fullstack-react/) and read away!

And man was I glad I did that - React is so cool!

I love how React uses encapsulated components to build UI. Having components own their own state and logic makes frontend development feel much better, especially compared to bare HTML/CSS/JS.

I’ll definitely be using React for frontend from now on!

### RESTful APIs with Flask

Unlike React, I’ve already made a few web applications with Flask prior to this project. Most of which were for my university classes. What’s different this time is that I’ll be building an API with Flask. 

Since I only know little about API development, I bought a copy of [RESTful Web APIs : Services for a changing World](https://www.amazon.com.au/RESTful-Web-APIs-Leonard-Richardson/dp/1449358063) and started learning.

One of the most memorable lessons I’ve learned is that REST wasn’t just for APIs but for the whole web. In fact, it was one of the key things that made the web what it is today. RESTful APIs are simply APIs that follow its constraints to reap the benefits it provides. 

I also learned what these benefits are, and the difference between RESTful APIs and RPC style APIs.

I thoroughly enjoyed the book, so much so that I might write about the lessons I’ve learned in greater detail in another article - so stay tuned for that if you’re interested!

In addition to API design and development, I also learned how to use Pytest with Flask. 

### Deploying for the First Time

One of the things I was really looking forward to in this project was learning how to deploy web applications. Up until now, all of the projects that I’ve completed are hosted on the local machine.

So I bought myself a server from Linode and started deploying away!

I’ve learned how to set up a web server with NGINX and configure it for both Flask and React applications. As well as how to set up HTTPS using Certbot. 


## One Step Closer to the Dream

Both storeUp and APInventory have been one of the most enjoyable projects I’ve ever done. 
All together it took me 4 months (started November 2021) to complete the project. Stumbling all the way to completion as I learned and practised new skills, and further developed current ones. 

While I’m obviously happy with my growth as a software engineer. It doesn’t come close to the feeling that I’ve helped not only myself and my problems, but also a community of people and a ministry that I love so dearly. I’m excited to see my team use my applications, and I’m even more excited to see how these tools will help the ministry and its people. 

To use my passion for software engineering to build tools that help and bring joy to people - that is the dream!

See you in the next project!


