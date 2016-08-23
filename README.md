# Web Application Architecture

## Introduction

Wikipedia defines a *web application* as follows:

> In computing, a web application or web app is a client-server software
> application in which the client (or user interface) runs in a web browser.

But this definition won't make any sense to you unless you know what a
*client-server* architecture is and what it takes to run a program in the
browser.

In this article, we're going to break this definition down and analyze each of
its components to understand the whole. The goal of this text is not to teach
how to hack out some frameworks and copy paste some pieces of code scattered
around the Web to build a web app. What it tries to achieve, is to give you the
big picture. It tries to answer two fundamental questions: How all these
technologies fit together and what computer science concepts are behind these
technologies.

## The Big Picture

**Note**: Don't panic if you don't understand few or even none of this section.
This section just tries to give an overview of what is going on when you
interact with a web app. Over the time and after playing with various pieces of
this puzzle, you'll start to understand each piece and it will feel less
intimidating. Thus, for the moment, focus on the procedure rather than the
details.

To simplify the process, let's assume that a web application is a website (you
will learn that a large number of websites are web applications but this
simplification isn't necessarily correct). What do you do to visit a website?
Well, you simply type the address of the website in the address bar of your web
browser and hit enter. After a few moments, (depending on your connection
speed) the website is loaded in the browser and you can interact with it. But
during those few moments mentioned earlier, a lot happened. First, your web
browser asked a DNS server what the corresponding IP address of the address you
just entered is. To make this happen, your browser made a UDP connection on the
port 53 to a pre-configured DNS server and sent a request. The DNS server
replied with a response containing the corresponding IP address of the website
(some thing like `216.58.211.14`). Having known the IP address of the website,
the browser made a TCP connection on the port 80 to the web server sitting at
that address and port. When the connection was established, the browser sent a
request for the website's home page using the HTTP protocol. After receiving of
the request by the web server, it responded with an HTTP response containing
the requested web page. Your browser received the web server's response and
tried to render the HTML web page but it turned out that there were some CSS
and JavaScript contents needed in order to fully render the web page. Again,
the browser made few HTTP requests asking the web server to send the required
contents and the web server delivered each request in separate responses. By
then, Your browser had the necessary pieces to render the web page. After
rendering the web page, the browser closed the TCP connection.

## What is a Web Application?

A web application is nothing more than a program that uses Web technologies to
receive input and send output. To get a better understanding of a web
application, let's consider a simple example. Suppose we have a website that its
only task is to show time of the day! Although this example may seem trivial,
it's a very good example of a dynamic website. To better understand what a
dynamic website is, one should know what a static website is. A static website
is a website that its content are static, which means that no matter who
requests its pages, it only shows the same pages again and again on every page
request. In contrast to the static website, a dynamic website generates its
pages on the fly. This means that there are no predefined pages to be delivered
to the requester. When a request comes for some page of a dynamic website,
there is a program that receives the request behind the scene and generates the
proper web page according to some parameters. This means that, for example, a
request for a web page located at `http://foo.com/bar` might end up being
differently generated for a user, say from Iran and another one from USA. A
dynamic web site is one kind of web application, since it uses Web
technologies. We said "one kind of Web applications" because there are other
Web applications that do not necessarily generate HTML content. For instance, A
web application might generate JSON output.

## What are Web technologies?

Web technologies are collection of various technologies that form the Web,
notably HTTP, HTML, CSS and JavaScript. These are the driving force behind the
Web. In the following section we will briefly look at these technologies.

## HTTP

*HTTP* stands for Hyper Text Transfer Protocol. It's a network protocol of the
application layer. Web browsers such as Firefox and web servers like Apache are
among the programs that understand this protocol. The exact mechanism of the
HTTP protocol is a bit complicated but a high-level view is as follows:

Before we explain the HTTP protocol, we should understand what a protocol is. A
protocol is a set of conventions that we use to convey our intentions. For
instance, the protocol that we use to make these information known to you, is
English but the protocol we use to communicate with, e.g. Iranians is Persian.
The protocol we use to instruct the computer is the CPU opcodes of it (all
programming languages instruction are eventually translated to CPU opcodes). One
of the protocols used among the computers to communicate in a network, is HTTP
(HTTP itself depends on some lower level protocols namely TCP and IP to
function).

Now that we have a fair understanding of what a protocol is, let's see how the
HTTP protocol works. HTTP works in a *client-server* manner. There is always a
computer that initiates an *HTTP request* called the client and another
computer that receives that HTTP request and responds to it with an *HTTP
response* which is called the server. HTTP requests come in seven forms but
currently we're only interested in two of them, *GET* and *POST*. When an HTTP
request is of the form GET, it's requesting some content from the server to
**get**. The server responds that request by sending the requested content to
the client. This is informally known as *downloading*. However, when the request
is of the form POST, the client is sending or **posting** some content to the
server. When the server receives the content from the client it responds with
message indicating that it successfully received the content.

Life would be easier if there were no errors. However, there is always a chance
of some kind of errors in every action, and HTTP is no exception. What if the
content we're requesting isn't available? What if the server's storage space is
full and cannot accept anymore content? To solve this problem the server sends
a *status code* to the client. You may have encountered the infamous *404*
status code when you request some web page that does not exist. This how the
web server informs the client of an error.

Every GET HTTP request, asks for a content. The content could be a web page, a
movie, a song and etc. The way that client requests the desired content is very
simple. The client starts its HTTP request with a line containing a line like
`GET /index.html HTTP/1.1`. This can be translated like this: I want to **get**
the index.html web page which is located at `/`. The `/`part is the address of
the content. So if were to request `bar.html` located at a directory such as
`foo`, it the address would be something like `/foo/bar.html`. You can see the
similarity between that address and the way your files are stored in a UNIX
(Linux) file system, and this is not a coincidence. The HTTP protocol was
invented on UNIX machines after all.

## HTML

Hyper Text Markup Language or *HTML* is not really a programming language but a
markup language. A markup language uses a special syntax to mark regions of the
text in order to give them a special meaning. For instance, HTML's bold tag
which is denoted by `<bold>` and `</bold>`, is used to mark a region of text to
be rendered as bold. When the whole text is marked up, it is fed to a renderer
(or sometimes a parser for further processing) to display. HTML, however, has
another advantage. A valid HTML text can be parsed and loaded into the memory
as a tree data structure which is called Document Object Model or DOM.

## CSS

A simple HTML is sufficient to draw text with simple elements such as bold text
and headers. But for more elaborate representation of text, it's not really as
capable. Cascade Style Sheet or for short *CSS* is a style sheet language that
can do the trick. It uses HTML tags' attributes id and class to operate on an
HTML text. Using CSS, one can position HTML elements (an HTML element is simply
an HTML tag) or change its color or size.

## JavaScript

In contrast to HTML and CSS, *JavaScript* is a full-blown programming language.
It is mostly used to manipulate the DOM but it can do whatever other programing
languages can. What is important, is that a JavaScript program is run on the
browser (e.g. Firefox) rather than the server. This is why it's called
client-side programming language, because it is sent uninterpreted to the
client. There is a JavaScript compiler in every web browser that compiles and
runs the received JavaScript code on the client machine.

## Frameworks

A web framework such as Django, Rails or CakePHP, is not a web technology in
sens of HTML or CSS but it plays a very fundamental role in web applications.
You may ask how a web framework fits in this configuration. To answer this
question, one should note that a web framework is nothing more than a set of
library functions and classes that facilitate generating dynamic content.
Dynamic contents like their static counterparts have URLs associated to them.
Back to our first example, when we enter `http://foo.com/bar`, `bar` is the
content that we request from the web server located at `foo.com`. When a
request arrives at the web server for some dynamic content, the server hands
off the request to the web framework that is already registered with the web
server for this particular URL. But the framework does not generate content on
its own. It's up to us to program the framework how to generate the desired
content. Running our program, the framework generates the response and gives it
to the web server to be delivered to the client. Building on this definition, a
web framework has two primary task. First, it should receive the HTTP request
from the server and calls the proper code to handle it. Second, it should
prepare a well-formated HTTP response containing the content generated by our
code to be given to the server.

Web frameworks tend to be written in scripting languages such as Python, Ruby,
PHP and the like because of their expressiveness and level of abstraction they
provide. Using the functions and classes provided by these frameworks, we can
program in the programming language of the framework to generate dynamic
content. For example, since Django is written in Python, we should program in
Python to call Django's API.

## Web Application Architecture Case Study

In this case study, we are going to look at *the Django web framework*. Django
is written in Python and has been around since 2005. The reason we chose Django
as our case study is that, while it's an industry standard web framework and
many huge web applications such as **Instagram** use it as their framework, it's
fairly simple and straightforward. One can, without having to delve into the
nitty-gritty details of it, start developing a simple web application to
understand the web application architecture.

## Django Primer

### Semantics

The first step to use Django is obviously to install it. To install Django, we
should use Python package manager `pip`. Beware that in Debian-based distros
such as Ubuntu, there are two `pip` commands. `pip` which is for Python version
2 and `pip3` which grabs and installs packages for Python 3. Since we use
Python 3 in our examples, we're going to use `pip3`. Normally it's not
installed by default. Let's install it first.

    sudo apt-get install python3-pip

Having installed `pip3`, we're ready to install Django:

    sudo pip3 install django

Done. We successfully installed Django. Next step is to setup the project.
Navigate to your home directory.

    cd ~

And issue this command:

    django-admin startproject helloworld

Now by listing the files through `ls`, we see that Django has created a new
directory named `helloworld`. The directory has the following structure:

    helloworld
    |-- helloworld
    |   |-- __init__.py
    |   |-- settings.py
    |   |-- urls.py
    |   `-- wsgi.py
    `-- manage.py

Let's `cd` into the `hellowrold` directory. Listing the directory, there is the
`manage.py` script by which we'll issue Django's commands. You can see that
inside the `helloworld` directory, there is another `helloworld` directory
containing some Python scripts. We're going to ignore them for the moment but
we'll get back to them later.

Although we haven't written any code yet, the machinery to run the web app is
OK. Thus we can run Django's *development server* to test it. Open up another
terminal, navigate to the project directory where `manage.py` is located and
enter this command:

    python3 manage.py runserver

It prints something like this:

    August 10, 2016 - 17:40:34
    Django version 1.9.5, using settings 'helloworld.settings'
    Starting development server at http://127.0.0.1:8000/
    Quit the server with CONTROL-C.

You may encounter with a line indicating that you have `unapplied migrations`
but it's not important. Your Django version may also be different from ours but
it's fine. The message shows that the development server is at
`http://127.0.0.1:8000/`. Open up your web browser and enter the address.
If everything goes well, it should show something like this:

    It worked!
    Congratulations on your first Django-powered page.

But what happened when you entered the address and hit enter? What happened is
**almost** similar to the section [The Big Picture](#the-big-picture) (We
suggest rereading that section).

For more investigation, put the web browser and the terminal window containing
Django's development server side by side. Refresh the web page in the browser.
You can see that whenever you refresh the page, two lines is printed in the
terminal window:

    Not Found: /
    [11/Aug/2016 08:21:28] "GET / HTTP/1.1" 200 1767

Let's talk about the second line first. It shows that an HTTP request has just
arrived at the web server requesting some resource at `/` (We'll explain `/` in
just a minute) and the web server has responded with no problem (the 200 is for
this reason). So if there was no problem serving the request, why does the
first line say "Not Found"? To get the answer, you should (re)read the section
[HTTP](#http). Building on what you learned in the HTTP section, you may notice
that the content (sometimes called resource) we requested from the server was
`/` which means no file is associated with this address (it should have been
something like `/foo.html`). This is something related to the dynamic nature of
the web applications that we'll cover it later in this article. The reason that
the first line says "Not Found: /", is that we requested the server to send us
whatever resource is associated with the address `/` and since that we don't
have any resources associated with this address, the server simply responded
with "Not Found". Django, however, is configured to respond with that default
page when there is no resource associated with the this particular address `/`.
To verify that, let's request another resource from the server. In the browser
address bar, enter `localhost:8000/hello`. You can see that the server responded
with:

    Page not found (404)
        Request Method:	GET
           Request URL:	http://localhost:8000/hello

Just as we expected.

Now, we're going to associate some content with the address `/hello`.  We need
a way to map the address `/hello` to some content. Open up the `urls.py` module
located at `helloworld/urls.py`. It's content is as follows:

```python
from django.conf.urls import url
from django.contrib import admin

urlpatterns = [
    url(r'^admin/', admin.site.urls),
]
```

The important part here is the `urlpatterns` list. `urlpatterns` holds a
mapping between URLs and **functions**. This is the key point. What
distinguishes static web sites from dynamic web sites, is this very function.
By mapping a URL to a function, we will be able to generate dynamic contents,
depending on how the function is programmed. To define a mapping between the
url `/hello` and a function, we can simply use the `url` function. This
function takes two parameters (actually many but currently we're concerned with
these two parameters). A string containing a URL and a function. But we don't
have any function yet, so let's create one.

Create a python module in the `helloworld` directory and name it something like
`functions.py` and define a function within it like this:

```python
from django.http import HttpResponse

def hello(request):
    return HttpResponse('hello')
```

Now that we have our function ready, let's map it to the `/hello` URL. Add a
`url`:

```python
from django.conf.urls import url
from django.contrib import admin

from .functions import hello

urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^hello/', hello),
]
```

And done. Let's see if it works properly. Enter `localhost:8000/hello` in the
browser. It should show a blank page with a `hello` in it.

But what happened when we requested `/hello` from the server? The server simply
passed the HTTP request to Django. Django looked up its registry to find if it
has any mappings from the address `/hello` to any function. Since Django found
one (the one that we defined earlier), it passed the request to our function
(that's why our function is defined with the parameter `request`. Every
function which is registered with Django, must at least accept one argument
which is the HTTP request).

We have our function working, but one important point remains. If look closer,
we'll find out that the `/hello` URL is not dynamic! On whatever request, our
function just returns hello. To add some dynamics to it, we can say hello and
show the time of the day.

```python
from django.http import HttpResponse
from django.utils import timezone

def hello(request):
    return HttpResponse('Hello, the time is: {}'.format(timezone.now()))
```

Now if you go to the address `/hello`, you'll see that with every request, the
response changes, which means we have a dynamic page.

### Representation

In the previous section, we successfully created a dynamic page that greets
people and shows time of the day. But what if we wanted to emphasize on time of
the day. Perhaps the time of the day part is more important to our visitors
than the greeting part. In other words, what should we do to show time of the
day in bold? Fortunately, HTML allows us to do the exact same thing. We can
mark (tag) the time part of the response that we want to be rendered in bold.

```python
return HttpResponse('Hello, the time is: <strong>{}</strong>'.format(timezone.now()))
```

After refreshing the page, we can see that the time is rendered in bold.

Putting an HTML tag in a python string might seem harmless in this tiny
example, but suppose we wanted to show greetings in many languages and local
times. That way, we would need a string of dozens of lines long with hundreds
of HTML tags in it, supposedly with in-line styles and scripts. Although it's
possible to put every thing in a string, it would definitely be a bad practice.
Dealing with quotations, escaping characters, improper syntax highlighting and
very long modules due to hundreds of HTML lines embedded in strings, would be a
nightmare. A very much better approach is to separate HTML from Python, in
other words, to separate **what** to show from **how** to show. Fortunately,
this separation is possible and Django provides it through what is known as
*templates*.

Templates are simply HTML files with some extra syntax known to Django. These
extra syntax act as place holders. In a function, we can produce some content
and pass them to Django along with a template file. Django then substitutes the
provided content with those place holders in the template. The act of
substituting place holders with content is called *rendering*. For instance, we
could change our function to use template similar to this:

First, we create an HTML file and put it in `helloworld/helloworld` where
`functions.py` is as well.

```html
<html>
  <head>
  </head>
  <body>
    <p>Hello, the time is <strong>{{ time }}</strong></p>
  </body>
</html>
```

Note the `{{ time }}` part. The `{{ }}` special syntax tells Django to replace
the `{{ time }}` part with the value of `time`.

Then, we should configure Django to find the template. Find the `TEMPLATES`
dictionary variable in the `settings.py` and populate the empty list of its
`DIRS` key with `BASE_DIR`. `TEMPLATES` should then look like this:

```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

And finally, we should use Django's `render` function to render our page.

```python
from django.utils import timezone
from django.shortcuts import render


def hello(request):
    content = {'time': timezone.now()}
    return render(request, 'time.html', content)
```

The `render` function, in addition to the request object, takes two other
arguments: a template file name and a dictionary containing the key/values to
be rendered. Note the `time` key of the content dictionary. It's must be the
same name as we previously defined in the template.

Now if we visit `localhost:8000/hello`, we'll see that everything works as
expected.
