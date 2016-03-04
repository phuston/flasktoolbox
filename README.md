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

Let's write some Flask. 

```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello World!'

if __name__ == '__main__':
    app.run()
```
