## NYCDA Backend Exam - Part 2

Given that we have a "customer" resource/model in our web server,

1 - How would you design the routes of your server based on REST convention? List them with VERB and /route

app.get - read
app.post - create
app.put - update
app.delete - destroy


2 - Which pages would require templates, and how would you name them? List them with /route and template-name.extension

edit.pug  - get/post/delete
show.pug  - get
index.pug - get
new.pug  - get/post

=========

3 - What is a database constraint? Name the 3 types of database constraints you have learned.

primary key - uniquely identifies each record in a database table
foreign key - points to a primary key in another table
not null - can not be null (empty)
unique - has to be unique, not the same value as in another column

4 - What is a foreign key? Given that you have a Factory that has many cars and car that belongs to a factory, What would be your foreign key column?

Foreign key has a relation to another table is out database. For example when we created our comments table, we needed it to have a relation to the posts table. So we created a foreign key on our comments table that could relate to the primary key in the posts table.

5 - List all the model lifecycle hooks you have learned from sequelize and explain them briefly if necessary.

Automatically called before/after model actions. We can use this to hash a password before updating it for example.

Callbacks on create:
before.validate
after.validate
before.create
after.create

Callbacks on update:
before.validate
after.validate
before.update
after.update

Callback on destroy:
before.destroy
after.destroy


6 - What is the difference between database-level validations and application-level validations?

One is made in the on a database-level and one in the application, it is a better practice to have a "fat model" rather than too many constraints on the db. If you change something in the model you don't need to run a migration. Also, the validations in the app runs before the database validations.

7 - Why do we use bcrypt. Write down 3 reasons why we use it if you can.

To secure the passwords in the database, if someone get access to our database, it will not see the password, but the encrypted version of it. Bcrypt is super slow which also makes it super hard to hack, compared to salting for example. Good for integrity.

8 - What is a flash message?

It can be for example a "pop-up" or just an alertbox that shows up with an error message, warning message, success message or information message.

9 - What is the difference between minifying and obfuscating JavaScript?

The goal of minifying is better performance and the obfuscating is to hide the original source code from other people.

10 - What are the 3 reasons that makes Gulp a good choice as an asset build library?

Reasons for using gulp:
- makes your front-end more readable to other developers
- it takes away the problem of repetition
- speed up your building process
