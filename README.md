# Web Application Architecture

## Introduction

Wikipedia defines a web application as follows: "In computing, a web
application or web app is a client-server software application in which the
client (or user interface) runs in a web browser". But this definition won't
make any sense to you unless you know what a client-server architecture is and
what it takes to run a program in the browser.

In this article, we're going to break this definition down and analyze each of
its components to understand the whole. The goal of this text is not to teach
how to hack out some frameworks and copy paste some pieces of code scattered
around the Web to build a web app. What it tries to achieve, is to give you the
big picture. It tries to answer two fundamental questions: How all these
technologies fit together and what computer science concepts are behind these
technologies.

## The Big Picture

Reminder: Don't panic if you don't understand few or even none of this section.
This section just tries to give an overview of what is going on when you
interact with a web app. Over the time and after playing with various pieces of
this puzzle, you'll start to understand each piece and they will feel less
intimidating. Thus, for the moment, focus on the procedure rather than the
details.

To simplify the process, let's assume that a web application is a website (you
will learn that lots of websites are web applications but this simplification
isn't necessarily correct). What do you do to visit a website?  Well, you
simply type the address of the website in the address bar of your web browser
and hit enter. After a few moments, (depending on your connection speed) the
website is loaded in the browser and you can interact with it. But during those
few moments mentioned earlier, a lot happened. First, your web browser asked a
DNS server what the corresponding IP address of the address you just entered
is. To make this happen, your browser made a UDP connection on the port 53 to a
pre-configured DNS server and sent a request. The DNS server replied with a
response containing the corresponding IP address of the website (some thing
like 216.58.211.14). Having known the IP address of the website, the browser
made a TCP connection on the port 80 to the web server sitting at that address
and port. When the connection was established, the browser sent a request for
the website's home page using the HTTP protocol. After receiving of the request
by the web server, it responded with an HTTP response containing the requested
web page. Your browser received the web server's response and tried to render
the HTML web page but it turned out that there were some CSS and Javascript
contents needed in order to fully render the web page. Again, the browser made
few HTTP requests asking the web server to send the required contents and the
web server delivered each request in separate responses. By then, Your browser
had the necessary pieces to render the web page. After rendering the web page,
the browser closed the TCP connection.

## What is a Web Application?

A web application is nothing more than a program that uses Web technologies to
receive input and send output. To get a better understanding of a web
application, lets consider a simple example. Suppose we have a website that its
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
technologies. We said 'one kind of Web application' because there are other Web
applications that do not necessarily generate HTML content. For instance, A web
application might generate JSON output.

## What are Web technologies?

Web technologies are collection of various technologies that form the Web,
notably HTTP, HTML, CSS and Javascript. These are the horse power of the Web.
In the following section we will briefly look at these technologies.

## HTTP

HTTP stands for Hyper Text Transfer Protocol. It's a network protocol of the
application layer. Web browsers such as Firefox and web servers like Apache are
among the programs that understand this protocol. The exact mechanism of the
HTTP protocol is a bit complicated but a high-level view is as follows:

## HTML

Hyper Text Markup Language or HTML is not really a programming language but a
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
capable. Cascade Style Sheet or for short CSS is a style sheet language that
can do the trick. It uses HTML tags' attributes id and class to operate on an
HTML text. Using CSS, one can position HTML elements (an HTML element is simply
an HTML tag) or change its color or size.

## Javascript

In contrast to HTML and CSS, Javascript is a full-blown programming language.
It is mostly used to manipulate the DOM but it can do whatever other programing
languages can. What is important, is that a Javascript program is run on the
browser (e.g. Firefox) rather than the server. This is why it's called
client-side programming language, because it is sent uninterpreted to the
client. There is a Javascript compiler in every web browser that compiles and
runs the received Javascript code on the client machine.
