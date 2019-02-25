---
layout: post
title:      "Notes on More Magical Code"
date:       2019-02-25 15:59:14 +0000
permalink:  notes_on_more_magical_code
---


## Or, a look at Corneal for Sinatra

The Flatiron Learn Web-Dev curriculum's second module poses us, the students, with the challenge of creating a webapp that allows users CRUD powers (create, read, update, destroy) over some input of their own. This app is to be created in a Ruby DSL (Domain Specific Language) called, of all things, "Sinatra"

<img src="https://media3.giphy.com/media/B8NSo2tYq4SRi/giphy.gif?cid=3640f6095c6ddb92746d5a482e5eacca" alt="Frank Sinatra Face GIF" width="200"/>

Sinatra purports to grant the ability to "[create] web applications in Ruby with minimal effort", displaying on [its home page](http://sinatrarb.com/) a code snippet which, theoretically, composes a (tiny) website in and of itself:
```
require 'sinatra'
    get '/frank-says' do
      'Put this in your pipe & smoke it!'
    end
```

And it's true, `ruby sinatra_app_name.rb` will let you look at one line of HTML on your localhost.

But as we've learned recently in the course, there is quite a bit of busywork involved in setting up a small, standard site. There's a config.ru file to be thought of for setting up [Rack](https://rack.github.io/),  [Shotgun](https://github.com/rtomayko/shotgun) or [Rerun](https://github.com/alexch/rerun) to run the app with. There's the whole model, view, controller system that a non-static website relies on, requiring sane directory structure and files for each. And there's the spec for doing test-driven coding. It's not exactly a mountain, but it is a pretty standard laundry list of code that, between projects, is not particularly DRY.

Enter the magic of [Corneal](https://thebrianemory.github.io/corneal/). Just as Bundler can spit out a mostly-ready template for an offline gem file, so Corneal preps a Sinatra CRUD app with a simple:
```
corneal new APP-NAME
```
APP-NAME appears in the current directory, complete with gemfile, rakefile, config.ru, MVC folders, and even a basic spec. What more could you want?

But wait, there's more! Enter:
```
corneal scaffold MODEL-NAME
```
And the desired model gains an empty class file *and* relevant views *and* relevant controller functions!
Needless to say, this is an incredible tool for quickly creating a bunch of small web apps within Sinatra. What better way to fail fast?

