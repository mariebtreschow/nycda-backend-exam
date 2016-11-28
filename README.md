## NYCDA Backend Exam
=====================
Explain the questions well!!

### 1- Why should we include script tags at the very end of an html file, before closing  ```</body>```?

It is the best practice. Since we want the page to load as fast as possible it is better to have the stylesheet downloaded first and then having the script tags with jquery and such loading after, otherwise it will try to download them all at the same time - slowing down the page.

### 2 - What is a middleware?
example:

app.get('/', (req, res, next) => {
   next();
   })

It has access to the req and res object. The function can end the req res cycle or just call the next middleware.
It acts between the server and the client and can execute any code.

### 3 - Why do we use express.static() middleware?

To serve static files such as CSS, images and JavaScript files.

### 4 - What is favicon.ico ?

Favicon is the little image on the tab of your website that you in the browser.

### 5 - Why do we use a bodyParser middleware ?

So that we can use: req.body in our functions/routes. It requires a whole body in the http request and then turn it into --> req.body

### 6 - What is the difference between parsing a data received from a web form with POST and an AJAX POST request?

They both run the same code, but the difference is the body parsing. Web forms serialize the data as formurlencoded format while AJAX POST request is a stringified JSON. Also both request would expect different type of responses, json request could receive a json response while web form requests generally receive redirect as a response and a status code.

### 7 - Why do we use methodOverride middleware ?

This overrides a method with another value, in our app we use it for deleting a post, so we turn the POST request to a delete or put.
It sass an optional key to use when checking for a method override, otherwise defaults to method.
The original method is available through req.originalMethod

String key --> returns Function

example:
form(action="/admin/posts/" + post.id method="POST
input(type="hidden" name="method" value="DELETE")

### 8 - What are the differences between sessions and cookies ?

Sessions are stored in the server and the cookies on client side. Sessions is a more secure way to store data.
Sessions can also hold objects, not just strings.

### 9 - Why do we use a session middleware ?

Because the session middleware let's use store and retrieve data on a per-site-visitor basis, it stores it on the server side and sends it as cookies. We use this for login with users for example. Sessions are accessible through the request object in each route. You can get and set properties just like you would when handling an object normally.

### 10 - Why do we use a build process ?

Making your front-end work a little easier to handle and build by for example minify.
