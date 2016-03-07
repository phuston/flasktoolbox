## Flask 

#### Introduction
Flask is a lightweight and powerful web framework for Python. It's easy to learn and simple to use, allowing you to build your web app in a short amount of time.

In this toolbox, you'll how to build a simple website, containing two static pages with a small amount of dynamic content. While Flask can be used for building complex, database-driven websites, starting with mostly static pages will be useful to introduce a workflow, which you can then generalize to make more complex pages in the future. Upon completion, you'll be able to use this sequence of steps to jumpstart your next Flask app.

#### Get Set
In this toolbox, you'll be learning Flask. To do this, you'll first need to install Flask. Run the following command:

`sudo pip install Flask`

#### What is Flask, Really?

In the introduction, we defined Flask as a 'web framework', but what does that actually mean? Let's dig deeper. Before this, let's develop a better understanding of how the internet works.

When you open up a web page in your browser (e.g. Chrome, Firefox, etc.), it makes an HTTP request to a server somewhere in the world. This could be something like `GET me the home page`. This server handles this request, sending back data (this can be in the form of HTML, JSON, XML, etc.), which is rendered by your browser. 

This is where Flask comes in - it allows you to create the logic to make a web server quickly in Python. You can write logic that will execute when a request is made for one of your routes (e.g. `www.mycoolwebsite.com/home`)

#### Hello World in Flask

Let's write some Flask. A simple Hello World application written in Flask can be as simple as this:

```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello World!'

if __name__ == '__main__':
    app.run()
```

Write this, save it as something like `hello.py`, and run it in terminal. Make sure to not call your application flask.py because this would conflict with Flask itself.

```
$ python hello.py
 * Running on http://127.0.0.1:5000/
```

Now head over to http://127.0.0.1:5000/, and you should see your hello world greeting.

In case you're curious `127.0.0.1` points to your local computer, and `5000` is the port it's listening on. 

What did that actually do? Let's walk through the steps.

1. First we imported the Flask class.
2. Next we create an instance of this class. The first argument is the name of the application’s module or package. If you are using a single module (as in this example), you should use __name__ because depending on if it’s started as application or imported as module the name will be different ('__main__' versus the actual import name). This is needed so that Flask knows where to look for templates, static files, and so on.
3. We then use the route() decorator to tell Flask what URL should trigger our function. In this case our route is `/`, commonly referred to as the `index` of a page. It refers to the 
4. The function is given a name which is also used to generate URLs for that particular function, and returns the message we want to display in the user’s browser.
5. Finally we use the run() function to run the local server with our application. The if __name__ == '__main__': makes sure the server only runs if the script is executed directly from the Python interpreter and not used as an imported module.

To stop the server, hit `ctrl+c`

#### What's this routing business?

In our hello world, example, we had one route denoted by the decorator `@app.route('/')`. Again, this 'decorator' tells the Flask app that any incoming requests for GET `/` will run the function we called `hello_world()`

Here are a couple more quick examples - 

```
@app.route('/')
def index():
    return 'Index Page'

@app.route('/hello')
def hello():
    return 'Hello World'
```

Pretty simple, right? What happens when we want to do something **useful** - e.g. display something other than text?

#### Let's Serve Some HTML!

HTML (HyperText Markup Language) is the standard markup language used to create web pages. In addition to sending back strings, Flask can send back HTML files to the client, which will be rendered in the browser. Let's get to work creating a basic HTML document. 

Let's start by creating a file called `index.html` 

```
<!DOCTYPE html>
<html>
   <head>
      <title>
         A Small Hello 
      </title>
   </head>
<body>
   <h1>Hi</h1>
   <p>This is very minimal "hello world" HTML document.</p> 
</body>
</html>
```

Create a new directory called `templates`, and save this new document as `index.html` there.

Let's figure out how to show this document now.
