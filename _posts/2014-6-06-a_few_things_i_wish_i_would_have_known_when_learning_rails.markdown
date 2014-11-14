---
layout: post
title:  "A few useful but lesser-known features of Ruby/Rails"
redirect_from: "/2014/6/06/pointlike/"
date:   2014-10-06 03:41:52
categories: rails ruby
---


General Rails Tips
================================

capture method (ActionView)


Gems
================================

# Environment

1. Use `rake -T` to view all available rake tasks. Including those
you've defined in /lib/tasks.

2. Use `rails s -p <port_number>` to override the default port Rails
uses on startup.

3. You can add ruby code to a `.railsrc` file in your home directory to
customize the behavior of the rails command.


Console Tricks
============================

1. You can customize your console by creating a .irbrc file (or .pryrc)

During startup IRB always attempts to load its runtime configuration
by a ruby file named `.irbrc` in your home directory. It then attempts to load the
.irbrc file in your working directory. 

This allows you to load your own startup
behavior create a .irbrc file (.pryrc if using Pry) and add whatever
ruby code you want executed when running the console.

Example (in .irbrc):

```

def some_method
  "only_visible_in_console"
end

a = "defined in .irbrc!"

```

```
$ irb
2.0.0p247 :001 > puts some_method
 => "only_visible_in_console"
2.0.0p247 :002 > puts a
 => "defined in .irbrc!"
```

last result = `_`

Example:

```
  >> username = User.first.name  # => 'Anthony'

  >> ans = _
  >> puts ans
  Anthony
  
```

2. Add a semicolon to the end of a statement to suppress default output

This is really useful for particularly verbose outputs that bury your
command history.

```
$ irb
2.0.0p247 :001 > "some result"
 => "only_visible_in_console"
2.0.0p247 :002 > "some result";
2.0.0p247 :003 > 
```

3. Use the .to_yaml method to view readable details of an object

```
$ irb
2.0.0p247 :001 > u = User.first;
2.0.0p247 :002 > puts a
 => "defined in .irbrc!"
```

4. Use the .explain or .to_sql on Active::Record::Relation methods to debug complex SQL queries
 
5. Use `reload!` to reload your console environment (IRB only)

6. Use console for composition not testing

7. Use Pry


# Production Environment

## Use multiple logs and use tagged logging


# Views:

## Use <%= debug(...) %> method in your views in development 

The debug method prints debug information about a variable within a
view. This is particularly important for front-end developers and QA testers
on your team in validating variables which are exchanged
between your views and controllers (such as params, session info,
cookies, queries, etc).   

Jose Valim has created a useful gem which extends this functionality
called RailsFootnotes. You can check it out here:
[https://github.com/josevalim/rails-footnotes]. It's also worth looking
at RailsPanel which is a Chrome extension for processing requests within
Rails.

# ActiveRecord

1. Use `find_each` when iterating over large recordsets

# General Ruby Tips (1.9.3 and higher)

2. You can use the `dup` method on any ActiveRecord object to create a
   deep copy

1. Use stabby lambda operator in place of lambda/proc `->() { }`

There's always been a bit of confusion between the difference between
lambdas and procs, the Ruby team has been trying to clarify this
confusion by introducing the `->() {}`

# Migrations
  Before committing, always use `rake db:migrate:redo` to ensure your migrations work well in
both directions and don't leave the schema in an inconsistent state. 



