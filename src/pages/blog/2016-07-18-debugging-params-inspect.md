---
templateKey: blog-post
path: debug-using-raise-inspect
title:  "Debugging Using Raise and Inspect"
layout: post
date:   2016-07-20T10:00:59.000Z
description: A blog post about debugging in ruby using raise and inspect.
---

Debugging is an important skill for a developer to have. When you are trying to figure the issue with a bug in your program, getting accustomed to various debugging techniques is important. This post will cover using the raise command in Ruby along with the `.inspect` method.

A common use case for this is when you want to inspect the params hash of a form. For example, let's say you have a rails form like so:

```
<h1>New Song</h1>

<%= form_for(@song) do |f| %>
  <%= f.label :title %>
  <%= f.text_field :title %>
  <%= f.label :release_year %>
  <%= f.text_field :release_year %>
  <%= f.label :genre %>
  <%= f.text_field :genre %>
  <%= f.label :artist_name %>
  <%= f.text_field :artist_name %>
  <%= f.label :released %>
  <%= f.check_box :released %>
  <%= f.submit %>
<% end %>
```

This would generate the following form:

![New Song Form](/img/params_inspect.png)

Let's complete the form:

![New Song Form Completed](/img/params_inspect2.png)

Now in the songs controller, create action let's raise an error and inspect the params hash.

```
def create
    raise params.inspect
    #rest of controller action code
```

Now when you submit the form you should get this:

![Project File Structure](./assets/img/params_inspect3.png)

And here you can see the params hash and inspect the various values for the song. This is a great way to debug and see if there are any unintended results. Not only can you view the params hash on this page, the terminal at the bottom of the browser will also allow you to play with the hash.

![Project File Structure](./assets/img/params_inspect4.png)

There are many other ways to debug and using raise-inspect is just one of them. Use it in good health!
