## Web Servers

Every web page is transmitted to your browser as `HTML` (a web markup language).
The application responsible for sending `HTML` to browsers is called a ***web server***.

***Confusingly enough**, the machine this application resides on is also usually called a web server*.

At the end of the day, all a web application does is send `HTML` to browsers.
(Sometimes, it also sends `css`, `js`, `png` depending upon the corresponding `GET` requests)


## HTTP

Browsers download websites from *web servers* (or "application servers") using the `HTTP` protocol.
The `HTTP` protocol is based on `request-response` model. The client(browser) *requests* data from
a web application that resides on a physical machine. The web application in turn *responds* to the
request with the data the browser requested.

An important point to remember is that communication is always instantiated by the *client*(browser).
The *server*(web server, that is) has no way of initiating a connection to you and send your browser data.
If you(browser) receive data from a web server, it is because your browser explicitly asked for it.


### HTTP Methods

Every message in the `HTTP` protocol has an associated *method*. The various `HTTP` methods correspond
to logically different types of requests the client can send, which in turn represent different
intentions on the client side. Requesting the HTML of a web page, for example, is logically different
than submitting a form, so the two actions require the use of different methods.


#### HTTP GET

The `GET` method does exactly what it sound like: gets(requests) data from the web server.
During a `GET` request the web application shouldn't need to do anything more that respond to do
anything more than respond with the requested page's HTML. Specifically, the web application should not
alter the state of the application as a result of `GET` request. (for example, it should not create
a new user account based on a `GET` request). For this reason, `GET` requests are usually considered "safe".

#### HTTP POST

There is more to interacting with web sites than simply looking at pages.
We are also able to *send* data to the application e.g. via a form. To do so,
a different type of request is required: `POST`. `POST` requests usually carry data entered
by the user and result in(lead to) some action being taken within the web application.
Signing up for a web site by entering your information on a form is done by `POST`ing the data
contained in the form to the web application.

Unlike a `GET` request, `POST` requests usually result in the state of the application changing.
In our example, a new user account is created when the form is `POST`ed. Unlike `GET` requests, `POST`
requests do not always result in a new HTML page being sent to the client. Instead, the client
uses the response's *response code* to determine if the operation on the application was successful.


### HTTP Response Code

In the normal case, a web server returns a *response code* of 200, meaning, "Everything went fine".
*Response codes* are always a three digit numerical code. The web applications must send one with each
response to indicate what happened as a result of a given request. The response code `200` literally means "OK"
and is the code most often used when responding to a `GET` request. A `POST` request, however, may result
in code `204`("No Content") being sent back, meaning "Everything went OK but I don't really have anything to show you."

It is important to realize that `POST` requests are still sent to a specific URL, which may be different from
the page the data was submitted from. From our signup example, the signup form may reside at `www.foo.com/signup`.
Hitting `submit`, however, may result in a `POST` request with the form data being sent to `www.foo.com/process_signup`.
The location a `POST` request should be sent to is specified in the form's `HTML`.


**NOTE:** This page is copied from [What is Web Framework?](http://jeffknupp.com/blog/2014/03/03/what-is-a-web-framework/)














