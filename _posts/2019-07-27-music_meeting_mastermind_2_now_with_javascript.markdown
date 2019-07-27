---
layout: post
title:      "Music Meeting Mastermind 2: Now with JavaScript"
date:       2019-07-27 17:27:07 +0000
permalink:  music_meeting_mastermind_2_now_with_javascript
---


And now, back to the previous Rails project!
It's been a crazy new world adding JavaScript to this project. There's more to delve into than I've quite mastered yet, but what does work feels really cool when it allows me to move around the app without reloading.

The basic principle being applied in this version of the project is the AJAX (Asynchronous JavaScript And XML) request. This is a style of http request wherein JavaScript being run on a browser makes a request on its own, and then uses the data it receives, usually without the browser refreshing. The main power of this technique, as I noted above, is that it can make a webapp feel like a desktop application without the start-stop feeling of refreshing. When the request is quick, it can respond as smoothly as a start menu. When the request takes longer, the JavaScript handles it asynchronously so that the user can do other things on the same page.

My own simple demo of this capability involves creating a straightforward feature that was lacking altogether from the Rails-alone project: The user account view/edit page. I split this idea into a system where users (and guests) can view non-personal user detail for anyone, but going to your own user page by default allows you to immediately edit and update the various aspects of your account.

Strangely enough, this has taught me as much about form builder and form submission in Rails as it has about JavaScript. The natural assumption of rails is that the user must submit an authenticity token along with any form, so that one cannot simply send a PUT or POST request to the server from anywhere. It is easy to build controllers that check for an appropriate user to be logged in before allowing the changes profferred, but it is still a sane default.

However, the need for a token created an interesting problem for my initial (and kind of unneccessary) design of having JavaScript files in the Rails pipeline that had html as plain text ready to deploy in various methods. If I were to have one form-creating method like:
```
renderForm(location) {
  $(location).append(`
	  <form>
		  ...
			`	)
		}
```
Then the form would not have the appropriate token. And so the views I created had a `<%= form_for ... %>` structure pre-created, and the `<script>` attached would put its forms into those tags.

Frustratingly, I have just now discovered that (of course!) Rails provides a helper method (`form_authenticity_token`) which I could have used to put said token anywhere on the page, leaving me more free to create the form however I liked.

But all of that is mooted by the further power of AJAX... It is by no means necessary to construct HTML strings in `<script>` tags, since JavaScript can ask a well-formed Rails controller to render pages and partials, just like a browser can!

If I create a view:
```
<%# _form.html.erb %>
<%= form_for @model do |f| %>
  ...
<% end %>
```

And a route:
```
# routes.rb
...
get "model/:id/edit_form", to "model#edit_form"
```

And an action:
```
# model_controller.rb
def edit_form
  render partial 'form'
end
```

I can simply have my JS ask for it:
```
// pageScript.js

  $.get("/model/1/edit_form").done(function(result) {
	  $("div.place").append(result)
	}

```
And it will appear in the `<div class="place">`
