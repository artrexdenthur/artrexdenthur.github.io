---
layout: post
title:      "Cutting a Gem"
date:       2019-01-07 15:14:52 +0000
permalink:  code_to_joy
---

*The Process for my Ruby CLI Project*

# A Step in the Right Direction

This first project, at the end of the Flatiron Learn Web Bootcamp's first module, has been a joy and a pain, a comfort and a challenge throughout this holiday season. As it draws to a close, I find it is also a project of which I am proud. Just as importantly, it was work of the type that I would gladly make a career in.
But enough waxing emotional. What follows describes this simple application and the work that went into it.

# Data in Harmony

My project is a simple CLI interface that scrapes certain areas of the [Barbershop Harmony Wiki](https://www.barbershopwiki.com/wiki/Barbershop_Wiki_Project) at the user's direction, storing the data found for perusal.
More specifically, the wiki contains information on various years of the Barbershop Harmony Society's premiere competition, "The International", separated into the categories of quartet competitors and chorus competitors. The CLI immediately scrapes the pages listing the champions by year for each of those types, then allows the user to view the parsed data by individual competitor or by type, or to request the interface to scrape and cache **all** the competitors from a given year (rather than just the winners).
The application's biggest limitation is that competitors' information consists only of the sites already scraped. This is because individual competitors' pages on the wiki are inconsistent, and so the logic to correctly gather their data would have taken prohibitively long to write.
Nevertheless, the functions that do exist work as I desired, and the [table generator gem](https://github.com/piotrmurach/tty-table) which I discovered makes the data printouts look rather nice indeed.

# Doing the Work

The process of this project involved various quantum steps in which a needed element of gem creation suddenly made sense (thanks usually to great documentation or explanations/help from instructors). When an element clicked into place like this, the next few steps fell into place almost by gravity.
From design to end, I remember the process looking like this:
1) Setting up the gem basics and the github repo
  Working with the gem creation process was certainly the most novel-feeling aspect of this project. Certainly it's the case that I still don't understand it fully, and will need to create more gems as I go. This particular project still relies on many gem creation defaults (e.g., there's no reason to change the laconic but correct description of this gem's install process), but I believe I understand the changes I did make.
2) Deciding on a data structure design
  The big trick here was deciding on metaphors for the data being gathered that would map as closely as possible onto the most efficient data structures. I ended up with the major data classes being as follows:
  * A Contest class that holds year and type data
  * A Competitor class with name and home district data, with Quartet and Chorus subclasses holding relevant data for their types (e.g. member list vs director name, respectively)
  * A Performance class. Each Contest or Competitor has many of the other through Performances. Every Performance has one Contest and one Competitor. It also holds score and rank data.
  This started out being just Competitions and Competitors. The two problems with this paradigm were that the names were confusing, and that each needed to have many of the other, for which a third class was needed to make the relationship work elegantly.
3) Building out the logic
  The rest of the actual program seemed fairly straightforward to me. Each needed feature seemed to be a loop of scrape the data correctly, load the data correctly, parse the commands correctly, and then display the data correctly, refactoring at the end of each loop if code was particularly egregious.
4) Testing and publishing
  This, like with the start, felt way more uncharted and uncovered various ways in which I did not quite understand gem, rake, and bundle. In particular, a few dependencies were off for the Linux system I was testing on. While fixing this I changed the version number a few times rather than figure out how to gem yank properly. In turn, this ballooned the size of my gem since each version began to take into account the previous compiled gems, which mightily slowed down the process until I discovered what the issue was.

# Done!

And so I have a [functioning gem](https://github.com/artrexdenthur/Ruby-Gem-Project-Barbershop-Contestants) May it be the first of many!
