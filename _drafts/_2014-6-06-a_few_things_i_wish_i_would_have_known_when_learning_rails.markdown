---
layout: post
blog_title:  "A few useful but lesser-known features of Ruby/Rails"
redirect_from: "/2014/10/05/a_few_things_i_wish_i_would_have_known_when_learning_rails/"
date:   2014-10-06 03:41:52
categories: rails ruby
---


## Gems/Environment

1. Use `rake -T` to view all available rake tasks. Including those
you've defined in /lib/tasks.

2. Use `rails s -p <port_number>` to override the default port Rails
uses on startup.

3. You can add ruby code to a `.railsrc` file in your home directory to
customize the behavior of the rails command.


###Console Tricks


####1. Customize the startup behavior in the console by creating a `.irbrc` file (or `.pryrc`) in your active directory

During startup IRB always attempts to run a ruby file named `.irbrc` in your current directory. If it isn't found, it recursively attempts to find it in each parent in directory tree, eventually defaulting to the `~/.irbrc` in your home directory if it exists.

This allows you to load your own startup behavior create a .irbrc file (.pryrc if using Pry) and add whatever
ruby code you want executed when running the console.

#### *Example (in `~/.../my_rails_project/.irbrc`):*

{% highlight ruby %}

def some_method
  "only_visible_in_console"
end

a = "defined in .irbrc!"

{% endhighlight %}

Code within this directory will then be run any time you load the console:

{% highlight ruby %}

~/.../my_rails_project > irb
...
irb > puts some_method
 => "only_visible_in_console"
irb > puts a
 => "defined in .irbrc!"
{% endhighlight %}

####2. Ruby saves the result of your most recent command in a special variable named `_`

Pretty self explanatory. Very useful if you forget to assign the result of a time consuming operation to a variable.

#### *Example:*

{% highlight ruby %}
irb > User.limit(1000).map {  |user| user.created_at }

irb > result = _
irb > puts result
...
  
{% endhighlight %}

####3. Add a semicolon to the end of a statement to suppress default output

This is really useful for particularly verbose outputs that flood your command history:

{% highlight ruby %}
$ irb
> user_sql_adapter = User.connection;
> raw_user_attributes = user_sql_adapter.execute("SELECT * from users");
{% endhighlight %}

4. Use the pretty print method with `.to_yaml`, `.to_a`, `.to_h`, `.to_json`, method to inspect an object.

{% highlight ruby %}
$ irb
irb > require 'pp'
irb > u = User.first;
irb > puts a
 => "defined in .irbrc!"
{% endhighlight %}

4. Use the `.explain` or `.to_sql` on `Active::Record::Relation` methods to debug complex SQL queries
5. Use `reload!` to reload your console environment (IRB only)
6. Use console for composition not testing
7. Use Pry


### Production Environment

### Use multiple logs and use tagged logging


# Views:

## Use `<%= debug(params) %>` and `<%= debug(session) %>` in your `application.html.erb` file

The `debug` method prints debug information about a variable within a
view. This is particularly important for front-end developers and QA testers
on your team in validating variables which are exchanged
between your views and controllers (such as params, session info,
cookies, queries, etc).   

Jose Valim has created a useful gem which extends this functionality
called RailsFootnotes. You can check it out here:
[https://github.com/josevalim/rails-footnotes]. It's also worth looking
at RailsPanel which is a Chrome extension for processing requests within
Rails.

#### ActiveRecord

1. Use `find_each` when iterating over large recordsets

2. You can use the `dup` method on any ActiveRecord object to create a
   deep copy

3. Use stabby lambda operator in place of lambda/proc `->() { }`

There's always been a bit of confusion between the difference between
lambdas and procs, the Ruby team has been trying to clarify this
confusion by introducing the `->() {}`

##### Migrations
  Before committing, always use `rake db:migrate:redo` to ensure your migrations work well in
both directions and don't leave the schema in an inconsistent state. 
