---
layout: post
title:      "Board Game Hoard"
date:       2019-03-09 23:29:48 -0500
permalink:  board_game_hoard
---


## My Sinatra Project

This project has been a great exploration of the basics of creating a website. I have by no means mastered it, but I have learned a lot on the way.

### The App Itself

My Sinatra webapp is called (Board Games Hoard)[https://github.com/artrexdenthur/board-game-hoard], and it is a simple interface for a user to create a list of their board games by name. Thanks to some much-appreciated configuration help from our cohort lead, Dakota, it is also hosted on (Heroku)[www.heroku.com], a lovely app-hosting site, at (https://board-game-hoard.herokuapp.com/)[https://board-game-hoard.herokuapp.com/].

The constant of the user interaction is at the bottom navs. These lead to indices for the user and game models. They also contain login, logout, and profile interactions depending on whether there is a user logged in.

Meanwhile, the organization of the whole site is as follows:

Welcome
* Users
  * Index
  * Show
* Games
  * Index
  * Show
* Login / Create User
  * Profile
  * Edit User
  * Edit / Create Games
					
Very straightforward. 

### Lessons Learned

#### ActiveRecord Validations

Many of the tools driving the requirements for the project come courtesy of ActiveRecord. For instance, the User model must have a name, email and password on creation. This is accomplished with the line:
```
validates_presence_of :username, :email, :password_digest
```
in the User class. The ActiveRecord Base model won't save an instance to the database if it fails to validate, which makes it easy to check a user's input and react to any problems:
```
  # path for creating a new user account
  post "/users" do
	  # Create a new User instance with the info given:
    user = User.new(email: params["email"], password: params["password"], username: params["username"])
		
		# Then see if it saves. If it didn't, go back to the user creation page. If it did, log the user in and show them their profile page.
    if user.save
      session[:user] = user
      redirect "/profile"
    else
      flash[:error] = user.errors.messages # This uses the excellent Sinatra "flash" messages gem!
      user.delete
      redirect "/users/new"
    end
  end
```

#### Session Secrets

I suspect one of the most valuable things I learned about is the concept of session secrets. The session secret is the key with which the Rack server encrypts a user's cookies. Martin Fowler has a good (writeup)[https://martinfowler.com/articles/session-secret.html] of how exactly one could gain admin access to a site by cracking a weak secret, like the string 'super secret' that the (Sinatra readme)[http://sinatrarb.com/intro.html] has (though it immediately goes on to explain proper security measures). 
Another problem appears in that my project is hosted on GitHub, and so the secret must not be in the code itself, or else it would be posted online for all to see. The dotenv gem allowed me to set it in a private, gitignored file.
However, that file naturally did not make it to the Heroku host, and so it had to be set there separately as an environment variable locked under my account.

#### Bootstrap

My site makes very little use of (bootstrap.css)[https://getbootstrap.com/], but I am excited to have learned for the first time about this library. I've definitely seen its theming around the internet, and, while it'll take work to make really distinct-looking websites with it, it seems like a solid foundation with which to make skeleton sites. I only wish I'd known about it sooner; while I'm glad I learned about the 'sinatra-flash' gem, bootstrap's automatic validation popups are so much cleaner-looking.

					 
