---
layout: post
title:      "Abstractions in Database Management"
date:       2019-02-07 16:13:55 +0000
permalink:  abstractions_in_database_management
---

## In which I learn about everyone's favorite anagram for CorrectedVia, ActiveRecord!

Having quickly been introduced to SQL, we've moved on to the use of SQL side-by-side with Ruby in the creation of ORMs. 

ORM (Object Relational Mapping) is a technique that allows for interface between type systems (usually a database's type system and a programming language's type system) by abstracting one of the type systems with objects. For example, one can take a simple database table like this:

![Songs database example](https://i.imgur.com/8yw5kz1.png)

And convert it to objects within (for example) Ruby with code like this:

``` ruby
class InteractiveRecord

  def initialize(options={})
    options.each do |k, v|
      self.send("#{k}=", v)
    end
    self
  end  
  
  def self.column_names
    DB[:conn].results_as_hash = true
    sql = "PRAGMA table_info('#{table_name}')"
    table_data = DB[:conn].execute(sql)
    # binding.pry
    table_data.map { |col| col["name"] }
  end
	
  def self.table_name
    self.to_s.downcase.pluralize
  end
	...
	```
	
This is the start of an inheritable class that provides ORM features to its children. A child of this class can immediately pull data from a connected database table that share its name but pluralized (that is, `class Song < InteractiveRecord` can access data in a `songs` table from a connected database). You can see the start of this in the column_names method which converts sql results into ruby data formats. Later methods convert this retrieved data to data stored in instances of the child InteractiveRecord class.
	
Once this is all set up, it is an incredibly useful way to manipulate the data which a database methodically stores with a scripting language like Ruby, which is much more fluid than SQL. Tedious SQL statements like 
``` sql
SELECT * FROM songs INNER JOIN artists ON artists.id = songs.artist_id WHERE artist.name = "Paul McCartney"
```
can be reduced to something closer to
``` ruby
paulM = Artist.find_by({name: "Paul McCartney"})
puts paulM.songs
```
Since an ORM will theoretically model joins as well, giving each subclass methods to self-assign relationships with other subclasses. This is much easier to read than the equivalent SQL and results in data structures which can be worked with programmatically.
	
But the amount of work involved in setting up such a system is significant, enough to steer one towards ad-hoc, one-time-use database queries in smaller projects.
	
Enter ActiveRecord, a [Ruby on Rails](https://api.rubyonrails.org/) library which provides all this ORM functionality. Not only does it connect classes automatically in just the same way as described above:
``` ruby
class Song < ActiveRecord::Base[5.1] # Song knows how to read from table song of connected database
```
but it also provides interfacing to the database in question:
``` ruby
DB = ActiveRecord::Base.establish_connection({adapter: 'sqlite3', database: 'db/songs.db'})
```

Furthermore, it can even keep track of and perform migrations to the database as it evolves. It's nice to know that its basic functions can be reproduced, but the ease that ActiveRecord provides in working with databases is astounding and highly useful. I'm excited to continue working with it in the future.
