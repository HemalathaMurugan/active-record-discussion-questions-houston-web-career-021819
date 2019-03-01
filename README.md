# ActiveRecord Discussion Questions

## Part One - Reading the Documentation

Looking at Documentation is an important part of programming. You don't have to memorize anything, but you should get familiar with the types of information you can find in different docs. For this exercise, go through the ActiveRecord documentation [here](http://guides.rubyonrails.org/active_record_querying.html#retrieving-objects-from-the-database) with your table mates and answer the following questions about each method.

1. What argument or arguments does the method take?
2. What type of object does the method return?
3. What happens if none of the parameters match? (i.e. what if `Tweet.find(5)` can't find that tweet? How about `Tweet.find_by(id: 6)`?

Methods:

1. `find`
  1. What argument or arguments does the method take?
    -id number
  2. What type of object does the method return?
    -array with one object, the class instance
  3. What happens if none of the parameters match?
    "The find method will raise an ActiveRecord::RecordNotFound exception unless a matching record is found for all of the supplied primary keys."

2. `.find_by`
  1. What argument or arguments does the method take?
    -column name and corresponding entry in that column
  2. What type of object does the method return?
    -instance of the class
  3. What happens if none of the parameters match?
    -returns 'nil'
      -"The find_by! method behaves exactly like find_by, except that it will raise ActiveRecord::RecordNotFound if no matching record is found."

3. `.where`
  1. What argument or arguments does the method take?
    -where is the most literal way to search with the part of an SQL query that would follow the WHERE in an SQL query, ex: Tweet.where("tweet_id = ?", id)
  2. What type of object does the method return?
    -instances
  3. What happens if none of the parameters match?
    -nil

4. `.all`
  1. What argument or arguments does the method take?
    -does not take arguments
  2. What type of object does the method return?
    -array of every instance in the table
  3. What happens if none of the parameters match?
    -there are no parameters

5. `.first`
  1. What argument or arguments does the method take?
    -none, or integer
  2. What type of object does the method return?
    -the first instance in that table, or an array of the first (integer) instances
  3. What happens if none of the parameters match?
    -returns 'nil'

6. `.destroy`
  1. What argument or arguments does the method take?
    -integer(s) that equals (an) id(s) in the table
  2. What type of object does the method return?
    -nil
  3. What happens if none of the parameters match?
    -? probably nothing, return nil


## Part Two - Name that SQL!

Pretend that you have a `tweets` table with two columns - `message` and `user_id`. Given the code below, write in a notebook or on a whiteboard what SQL statements will fire when the following methods are called?

```
class Tweet < ActiveRecord::Base

end
```

1. `Tweet.all`
  -"SELECT * FROM tweets";
2. `Tweet.find(5)`
  -"SELECT * FROM tweets WHERE tweets.id = 5 LIMIT 1";
3. `Tweet.find_by(user_id: 7)`
  -"SELECT * FROM tweets WHERE user_id = 7 LIMIT 1";
4. `Tweet.where(user_id: 7)`
  -"SELECT * FROM tweets WHERE user_id = 7 LIMIT 1";
5. `Tweet.create(user_id: 5, message: 'making some coffee')`
  -"INSERT INTO tweets (user_id, message) VALUES (5, 'making some coffee')";
6. `Tweet.destroy(7)`
  -"DELETE FROM tweets WHERE tweets.id = 7";
