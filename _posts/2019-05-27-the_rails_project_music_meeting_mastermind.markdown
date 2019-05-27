---
layout: post
title:      "The Rails Project: Music Meeting Mastermind"
date:       2019-05-27 23:52:33 +0000
permalink:  the_rails_project_music_meeting_mastermind
---

## This one is a bit like a real thing, isn't it?

With this blog post I am almost entirely finished with the third of five modules for the Flatiron Software Engineering course. It's been an exciting project, and a clear step up in complexity from either the [CLI app](https://artrexdenthur.github.io/CLI_process) or the [Sinatra webapp](https://artrexdenthur.github.io/board_game_hoard).
The site is not live to the public as of this posting, but it looks and feels a little bit more like an actual website than anything I've done, and I'm sort of proud of that.

## Time Management

The biggest deal with this project has been that it has taken place in the midst of a myriad of other equally important projects in my life, and I am turning it in basically right under the wire at maximum lateness before consequences. Phew! So it's appropriate to talk about what I've learned about time management, at least things I think will help with this going forward.

#### Do a little every day
Whenever I could get a streak of days doing even half an hour, the project started to go much more smoothly. But a lot of the time, that seemed impossible because of my other projects, until I started to use...

#### Calendar Blocking
Everything important to me has its spot on Google Calendar. I don't panic if I don't follow it exactly, but having everything written out like that makes it easy to see how I'm going to get that ever-important half-hour in on x, y, and z crazy days.

#### Learn to write tests
This is still something I don't do well, but I demonstrably would have saved a lot of time if I'd had a test suite to keep me on track. A lot of the time I had my mind going around three different vaguely-defined problems, and running tests like in the program's exercises would have helped me ground my understanding of the most important next steps.

#### Bonus: Setting up other machines
It was really important for me to be able to work on the project wherever I needed to be, which meant having a setup prepared on machines other than my immobile main computer. It was especially helpful in the run-up to the project to have the learn-co gem installed... Well worth the effort.

## Rails Itself

So, what exactly is [Ruby on Rails](https://rubyonrails.org/)? It's a web application framework that, like Sinatra, brings together a plethora of useful gems and its own DSL's to provide what is, for many users and purposes, a balance between the extremes of writing every component of a  website from scratch, and having to work with a quick-and-easy but unconfigurable interface.
Sinatra itself depends on portions of Rails (especially ActiveRecord). Rails is much bigger than Sinatra though, being composed of modules that work together to form an MVC interface. Rails infuses an application's models with useful code and works as a layer between the database and the running app. It also provides sane but easily-configurable defaults for RESTful resource routing and view organization.

## Music Meeting Mastermind

My app in particular is inspired by one I use often, (Choir Genius by Groupanizer)[https://www.choirgenius.com/]. The idea of Choir Genius is to provide choirs with both members-only and public-facing websites, with lots of features tailored to choral needs. 
My app (Music Meeting Mastermind) is not nearly so feature-packed, but takes the form of a simple content management site wherein users can create choruses, fill them with singers, and join other users' choruses. 

I've learned many useful lessons in the process of building this, including:

#### Partials are awesome

Rails allows any view response to, via erb, interrupt itself with another template. This is a great timesaver and code DRYer since, as the official Rails guides [suggest](https://guides.rubyonrails.org/layouts_and_rendering.html#using-partials), you can use a partial template like you would a subroutine. For a cms, a must-implement pattern with partials is a form partial. This allows your 'new' and 'edit' templates for a given resource to be just a few lines long, calling the same form partial on one of their lines. Since creating a new resource and editing it almost always access the same fields, this is a straightforward way to DRY up code, and to allow for more flexibility if changes are made. If, for example, you add a footer to your post model, the partial pattern allows you to just change the form, and both the new and edit views instantly will have the footer.

I found this especially helpful when I ended up with various levels of nesting in my models. When editing a User, I wanted to be able to modify the Profile (a different model), and so the profile form partial could be nested into the user form partial, as well as being used for modifying profiles directly (since they could be detached from users).

#### Don't take a css/javascript template for granted

I decided to use [Materialize](http://materialize.labs.my) for my site, and while it looks much better for it, it had some quirks that did unexpected things. For instance, I needed drop-down selections for certain forms. Materialize, naturally, has its own slick JavaScript settings for animated drop-downs, but they only go off if your html is "just so" (I could never get that to work), and at the same time the Materialize css hides drop-downs entirely (and silently!) in all cases, even when its JS doesn't work. This resulted in some good time spent looking for the one class option (class="browser-default") that is allowed through.

## Parting Notes

This has been a fun project and I'm happy to have completed the requirements. I'm very glad that we get to iterate on this same project in the JavaScript section, since I know it can be better than it is and would love to add more to it.
On the whole I think I've learned a lot, and learned a lot about how far I still have to go. Hope you learned something from this too. Happy coding!


