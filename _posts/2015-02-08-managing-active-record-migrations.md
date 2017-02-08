---
layout: post
blog_title:  "Some short and simple tips on maintaining migrations in Rails"
title: "Blog"
redirect_from: "/2015/02/01/maintaining-migrations-in-rails"
permalink: "blog/maintaining-migrations-in-rails"
date:   2015-02-08 10:09:31
categories: rails migrations database
---

A common pain point for any web developer is maintaining DB schema consistency as the complexity of an application grows.
Even though Rails provides migrations as a framework for managing changes to a database schema, problems can still arise especially
when managing an app that has multiple environments or is maintained by a large development team.

**Here are a few simple steps I follow when writing a new migration:**

##### **1. Start from a clean git state (i.e. `git status` says "nothing to commit").**


{% highlight ruby %}
$ git status
On branch hubspot_integration
Your branch is up-to-date with 'origin/hubspot_integration'.
nothing to commit, working directory clean
{% endhighlight %}

It's important to isolate all migration/schema changes commits in a single commit. This is important not only for the
readability/maintainability of your git history however, but more importantly we want to closely track all changes to `schema.rb`.

---

##### **2. Explicitly define both the `up` and `down` methods of the migration.**


{% highlight ruby %}
class RemovePlaintextColumns < ActiveRecord::Migration
  def up
    remove_column :payment_accounts, :bank_account_number, :string
    remove_column :payment_accounts, :tax_id, :string
  end

  def down
    add_column :payment_accounts, :bank_account_number, :string
    add_column :payment_accounts, :tax_id, :string
  end
end
{% endhighlight %}

In other words don't rely on the `change` to do what you expect it to. The reasoning here is simple: it's best to be
explicit, especially considering that migration behavior can vary across database implementations.
Also, the `change` method isn't guaranteed to implement the `db:migrate:rollback` action correctly. An example of this
is if you declare something like `remove_column :users, :middle_name`, Rails won't know how to reverse the removal because
 the column type information isn't specified.

---

##### **3. Run `rake db:migrate` immediately followed by `git status` to ensure the changes made to `schema.rb` are consistent with your expectation.**

You'll see the timestamp change along with changes in the respective tables affected by the migration.

---

##### **4. Use `git add .` to add all changes made by the migration to the git staging area. *Don't commit yet.***

The reasons for this will be obvious after the next step.

---

##### **5. Run `rake db:migrate:redo`**

If both your `up` and `down` methods are correctly defined then there should be no changes in our working directory and
therefore `git status` shouldn't show any unstaged changes. In other words, your migrations are idempotent and didn't
affect the schema when run more than once.

---

##### **6. If all goes well, commit the changes and summarize the commit changes within the body of the commit message.**

#### *If you encounter an error during the migration or get stuck in a consistent state:*

  - If you're getting some error along the lines of 'column doesn't exist' etc. then wrap the offending line of code in an `if` statement using the `table_exists?` and `column_exists?` to ensure that the migration doesn't run against columns that have been deleted.
  - Your development should have a properly defined seeds file where `RAILS_ENV=development rake db:reset` can be run to wipe and reinitialize the application into a usable state. If shit really hits the fan, it may be worthwhile to discard the commit and run a `rake db:reset` the database, but be warned that this drops the database so it should always be used judiciously.

---

##### **Some final points**
  - Never make a commit unless both `rake db:migrate` && `rake db:migrate:redo` run as expected without errors.
  - Be absolutely sure your development environment is well isolated from staging/production environments
  - Run `rake db:migrate:status` and cross reference the printed result with the timestamp in `schema.rb` to make sure you are where you think you are.
  - Never make changes to schema.rb directly, this will only make things worse.
  - Avoid editing any migrations run before the commit made in step 1.
  - Run `rake db:setup` regularly to ensure your database migrations and seed files can reproduce a workable development environment.
  - Be wary of using `rename_column`, `remove_column`, they can both cause errors and downtime.
  - When renaming a column in a SQL DB, the table containing the column is locked until the rename completes, which, depending on the size of the table, can cause deadlocks in production. Similarly, ActiveRecord often stores columns in a cache meaning columns can still be referenced even after. Manual Weiss of Codeship has a much more thorough discussion on this on his blog: http://blog.codeship.com/rails-migrations-zero-downtime/

