---
layout: post
blog_title:  "Some useful, lesser-known features of the Ruby/Rails console"
redirect_from: "/2014/06/06/some-useful-lesser-known-features-of-the-ruby-rails-console.markdown/"
permalink: "blog/rails-console-tips"
date:   2014-10-06 03:41:52
categories: rails ruby
---
###1. Customize the startup behavior in the console by creating a `.irbrc` file (or `.pryrc`) in your active directory

During startup IRB always attempts to run a ruby file named `.irbrc` in your current directory. If it isn't found, it recursively attempts to find it in each parent in directory tree, eventually defaulting to the `~/.irbrc` in your home directory if it exists.

This allows you to load your own startup behavior create a .irbrc file (.pryrc if using Pry) and add whatever
ruby code you want executed when running the console.

##### *Example (in your `my_rails_project/.irbrc` file):*

{% highlight ruby %}

def some_method
  "only_visible_in_console"
end

a = "defined in .irbrc!"

{% endhighlight %}

Code within this directory will then be run any time you load the console:

{% highlight ruby %}

my_rails_project> irb
...
irb > puts some_method
 => "only_visible_in_console"
irb > puts a
 => "defined in .irbrc!"
{% endhighlight %}

###2. Ruby saves the result of your most recent command in a special variable named '`_`'

Pretty self explanatory. Very useful if you forget to assign the result of a time consuming operation to a variable.

##### *Example:*

{% highlight ruby %}
irb > User.limit(1000).map {  |user| user.created_at }

irb > result = _
irb > puts result
...
  
{% endhighlight %}

###3. Add a semicolon to the end of a statement to suppress default output

This is really useful for particularly verbose outputs that flood your command history:

{% highlight ruby %}
user@localhost:> irb
> user_sql_adapter = User.connection;
> raw_user_attributes = user_sql_adapter.execute("SELECT * from users");
{% endhighlight %}

###4. Use the pretty print method (`pp`) to inspect the properties a hash:

{% highlight ruby %}
~/.../my_rails_project> irb
irb > require 'pp'
irb > user = User.first;
irb > puts user.attributes
{% endhighlight %}

####5. Use the `reload!` method to update code changes made outside of the console

Again, pretty self-explanatory, but extremely useful to know as well.


