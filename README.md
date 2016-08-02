# Web Application Architecture

## Introduction

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
request for a web page located at http://foo.com/bar might end up being
differently generated for a user, say from Iran and another one from USA. A
dynamic web site is one kind of web application, since it uses Web
technologies.

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
