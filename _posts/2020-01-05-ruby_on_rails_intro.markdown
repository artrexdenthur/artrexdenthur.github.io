---
layout: post
title:      "Ruby on Rails Basics"
date:       
permalink: ruby_on_rails_intro
---


A quick intro into my server-side web development framework of choice

## Intro: Definitions

What is Ruby on Rails, at its simplest? It is a Ruby framework for writing server-side web applications with a model-view-controller paradigm. 

Let's break that down.

### Ruby

[https://www.ruby-lang.org](Ruby) is a high-level object-oriented programming language developed by Yukihiro "Matz" Matsumodo. Matz developed it in order to create a language that he himself would enjoy programming in, and accordingly one of its hallmarks is the attempt to follow the "Principle of Least Astonishment". This principle dictates that, in a programming language, the method by which any given action is taking should cause as little surprise or astonishment in the user as possible. A good example of this paradigm is a contrast between the interactive consoles of Ruby and Python, another high-level language which is often compared with Ruby:

```
$ irb
irb(main):001:0> exit
$ irb
irb(main):001:0> quit

$ python
>>> exit
Use exit() or Ctrl-D (i.e. EOF) to exit
```

In the first example, we see that the Ruby interactive console responds to simple 'exit' and 'quit' commands in an expected fashion. Python creates surprise not only by not accepting an 'exit' command, but by giving an error message that clearly understands the intent of the user and insists on an only slightly different command.

### Server-Side Web Applications

A Server-Side framework is contrasted with Client-Side, and each describes where the code is running that creates the user's experience of a web application. A Server-Side framework waits on the creator's server for a remote user request, creates the web page needed, and sends it across the internet to the user. Client-Side code and frameworks are usually JavaScript-based, and are usually packaged up by Server-Side code, sent across with the web page, and then provide logic that the user can take advantage of without making additional conventional requests to the remote server. Ruby on Rails has systems for managing and serving Client-Side code in the form of gems that handle JavaScript, CoffeeScript, and related frameworks, but the core of Ruby on Rails is meant to run a server and handle remote requests.

### Model-View-Controller

Model-View-Controller is a web application programming paradigm that separates code concerns into the three named parts. Code in the Model handles server-side business logic, code in the View is responsible for directly creating web pages, and code in the Controller translates user interactions to the Model and the View. This is often better understood through a food service metaphor:
The Controller is like a waiter. A customer enters the restaurant (website) and the waiter directs them to a table (the View), which initially just has a menu (the homepage). The customer selects a meal (clicks on an internal link), and the waiter asks the chef to make the food (the Controller channels user input to the Model's business logic), then brings the completed meal back to the table (displays the results to the user).
This paradigm is, in general, arbitrary and it is up to the designer to make use of it as appropriate to the project. Rails in particular does make it easy to use the paradigm, though, by creating different kinds of files and interactions by default. The easiest way to code a website in Rails without changing these defaults is to use an MVC paradigm.