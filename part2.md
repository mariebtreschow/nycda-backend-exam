## NYCDA Backend Exam - Part 2

Given that we have a "customer" resource/model in our web server,

1 - How would you design the routes of your server based on REST convention? List them with VERB and /route


router.get('/customer', (req, res) => {
   db.customer.findAll({ order: 'id DESC' }).then((customer) => {
      res.render('customer/index', { customer:customer });
   });
});

router.get('/customer/edit', (req, res) => {
   db.customer.findAll({ order: 'id DESC' }).then((customer) => {
      res.render('customer/edit', { customer: customer, user: req.session.user });
   });
});

router.customer('/customer', (req, res) => {
   db.customer.create(req.body).then((customer) => {
      res.redirect('/' + customer.slug);
   }).catch((error) => {
      res.render('customer/new', { errors: error.errors, user: req.session.user })
   });
});

router.get('/customer/new', (req, res) => {
   res.render('customer/new', { user: req.session.user });
});


router.get('/customer/:id/edit', (req, res) => {
   db.customer.findOne(req.body, {
      where: {
         id: req.params.id
      }
   }).then((customer) => {
      res.render('customer/edit', { customer : customer, user: req.session.user });
   });
});

router.put('/customer/:id', (req, res) => {
   db.customer.update(req.body, {
      where: {
         id: req.params.id
      }
   }).then(() => {
      res.redirect('/admin/customer');
   }).catch((error, customer) => {
      res.render('customer/edit', { errors: error.errors, user: req.session.user, customer: customer });
   });
});

router.delete('/customer/:id', (req, res) => {
   db.customer.destroy({
      where: {
         id: req.params.id
      }
   }).then(() => {
      res.redirect('/customer');
   });
});


module.exports = router;

2 - Which pages would require templates, and how would you name them? List them with /route and template-name.extension

edit.pug  - get/customer/delete
show.pug  - get
index.pug - get
new.pug  - get/customer

=========

3 - What is a database constraint? Name the 3 types of database constraints you have learned.

primary key - uniquely identifies each record in a database table
foreign key - points to a primary key in another table
not null - can not be null (empty)
unique - has to be unique, not the same value as in another column

4 - What is a foreign key? Given that you have a Factory that has many cars and car that belongs to a factory, What would be your foreign key column?

Foreign key has a relation to another table is out database. For example when we created our comments table, we needed it to have a relation to the customer table. So we created a foreign key on our comments table that could relate to the primary key in the customer table.

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

One is made in the on a database-level and one in the application. It is better to have many constraints on the database rather than in the model.

7 - Why do we use bcrypt. Write down 3 reasons why we use it if you can.

To secure the passwords in the database, if someone get access to our database, it will not see the password, but the encrypted version of it. Bcrypt is super slow which also makes it super hard to hack, compared to salting for example. Good for integrity.
Bcrypt compare two hashes.

8 - What is a flash message?

It can be for example a "pop-up" or just an alertbox that shows up with an error message, warning message, success message or information message.

9 - What is the difference between minifying and obfuscating JavaScript?

The goal of minifying is better performance and the obfuscating is to hide the original source code from other people.

10 - What are the 3 reasons that makes Gulp a good choice as an asset build library?

Reasons for using gulp:
- makes your front-end more readable to other developers
- it takes away the problem of repetition
- speed up your building process
