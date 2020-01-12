---
layout: post
title:      "Ruby on Rails Basics - Part Two"
date:      2020-01-11 18:58:28 +00:00 
permalink: ruby_on_rails_intro_part_two
---

The second part of an intro into my server-side web development framework of choice

## Why Ruby on Rails?

In my [previous entry](ruby_on_rails_intro_part_one) I talked about the bare definitions of the [Ruby on Rails](https://www.rubyonrails.org) framework. Here I'll go into detail on the features that set it apart and the reasons you may or may not wish to use it.

### Ease of Use

One of Ruby on Rails' biggest draws is the fact that it enables developers to quickly get professional quality websites up and running with ease. This stems from one of its basic design tenets, ["Convention over Configuration"](https://rubyonrails.org/doctrine/#convention-over-configuration). The `scaffold` tool in particular can generate essentially a whole site with a simple command, and more granular generation tools exist for those with more need for customization. These tools seek to empower the developer with tested patterns.
Another Rails design tenet, ["Provide sharp knives"](https://rubyonrails.org/doctrine/#provide-sharp-knives), provides a balance to the focus on convention. Rails, as with Ruby, not only allows the advanced designer to easily opt out of convention with modular code (as in the following section) but even to "monkey patch" core Ruby classes and methods. These two choices together make Rails an easy system to use both for the novice and for the expert.

### Expandability

Just by being written in Ruby, Rails inherits a library of code in the form of Ruby gems, which is a repository that occupies somewhat of a "sweet spot" in terms of variety. Node.js is of course king for absolute number of options, but the medium-sized library that Rubygems represents can in most cases provide just as strong support since the community magnetizes behind a focused set of (still diverse) options.

### Reliability

Rails, in all its versions, is no longer one of the hot new frameworks, and it benefits from that in increasingly bearing the mantle of the "tried and true". The newest versions have worked out many kinks and have a dedicated user base to explain old problems and attack new ones.
Not only that, but one of Rails' core components is an integrated testing library, providing developers with the tools to ensure that their own solution is running as expected.

### Ruby

Naturally, one benefits from developing in a familiar language. In a smaller development team, if most of the developers are most familiar with Ruby it is likely that Ruby on Rails will be one of their best options, given that there are no other Ruby web frameworks with even close to the same amount of support. Sinatra may be an option, but only for the smallest of projects, since it is designed to be lightweight and provide only the bare minimum of features.

## Other Options

So, what if the cons outweight the pros? A few options are scattered through the above discussion, but here is an organized list highlighting some of the major alternatives.

### Sinatra

![](http://woodiwiss.me/content/images/2016/07/sinatra.jpg)

If you have a project that you want to be highly self-configured, and especially if it happens to be (or needs to be) quite small, [Sinatra](https://www.sinatrarb.com/) might be a good one to check out. It even describes itself as a DSL rather than a framework, so expect the lightweight and all the pros and cons that come with it. Still, Rubygems remains an advantage for Sinatra, and so a 

### Django

[![Django Logo](https://cdn.iconscout.com/icon/free/png-256/django-12-1175186.png)](https://www.djangoproject.com/)

But what if you like the sound of Rails, but are a Python expert not looking to pick up a new language? [Django](https://www.djangoproject.com/) may be a worthwhile option. Django boasts similar community engagement and a Python-appropriate "batteries included" philosophy. That is, with this framework there is expected to be similarly quick setup to Ruby on Rails, since a full suite of tools is included, and many choices are defaulted to speed up development.

### Symfony

[![](https://symfony.com/logos/symfony_white_02.svg)](https://symfony.com/)

Finally, what if Rails doesn't have enough for you? Your enterprise-class web application needs to be highly configured from the ground up, and your team has as much time as they need to develop it. A popular option for this sort of project is the PHP framework [Symfony](https://symfony.com/). Symfony exposes a plethora of configuration options at every step along the way, and its systems are decoupled from each other for maximal customizability. 