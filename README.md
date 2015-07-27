# Hat-Tip

## Learning Competencies

 * Understand what an HTTP client sends to a server
 * Understand what an HTTP server sends to a client
 * Understand how HTTP servers and clients interact

**Note:** The point of this challenge is to learn about HTTP. Keep the competencies in mind and allocate your time accordingly.

## What's HTTP?

HTTP is a protocol. In this case the protocol is simply an agreement between programs that they'll send **text** to each other in a **specific format** via a **TCP connection**. You already know what TCP connections are, and you know how to send text over them. So, understanding HTTP is just a matter of understanding the text format that HTTP requests and responses are sent in.

## Release 1, an HTTP client

### The Request Format

Let's talk about the "specific format" of an HTTP request. Here's an HTTP request that fetches `http://devbootcamp.com/locations/chicago/`.

   ```
   GET /locations/chicago/ HTTP/1.1
   Host: devbootcamp.com

   ```

The text you see above is the same text your browser sends to the devbootcamp.com server over TCP. There's no magic here, the web is just a matter of formatting requests and responses correctly so that everybody can communicate.

The format of a request is pretty simple. We have the HTTP request type (`GET`) followed by the thing we want (`/locations/chicago`), followed by the HTTP version (`HTTP/1.1`).

On the next line we specify the `Host` as `devbootcamp.com`, the server we're connecting to.

Last but not least, we send an empty line. This is important! That empty line is how the browser tells the server "I'm done sending you data about my request."

There are many different kinds of HTTP request types but the simplest of all is the humble `GET` we see above. `GET` just says "give me this thing I'm looking for." A `GET` is what happens every time you type a URL into your browser.



### Write your Client

Write a program that sends a GET request over TCP to `www.example.com` on port 80 to fetch the `/index.html` page on the server.

Your client should print out the lines that it gets back from the server.

## Release 2, an HTTP server

In the last release you wrote a basic HTTP client that accessed a real-life-website and displayed its contents (which is pretty amazing).

In this release let's write a little HTTP _server_. We'll connect to it with Chrome, our favorite HTTP client.

### Requirements

Your server should run on port 2000. You can tell Chrome to visit it by going to the url  `http://127.0.0.1:2000/` once you have it up and running.

The _simplest_ response your server can send is a classic `200 OK`, which says "I have the thing you're looking for, here you go."

```
HTTP/1.1 200 OK
Content-Length: 130

<html>
<head>
  <title>An Example Page</title>
</head>
<body>
  Hello World, this is a very simple HTML document.
</body>
</html>
```

As you can see, a `200` response needs (at least) three pieces.

 * The response line indicating that this is, in fact, a `200` response
 * A line specifying the length of the content that will be sent back in characters (bytes)
 * An empty line
 * A series of lines representing the content.

If your TCP server is sending the example above correctly, you should be able to visit your server in Chrome and see the web page!

## Release 3, Expand the Server

Change your server to serve two simple pages.

 * `/hi` should send back a response with a greeting
 * `/quote` should send back a quote of your choosing

Visiting `http://127.0.0.1:2000/hi` should give you one of these and `http://127.0.0.1:2000/quote` the other.

**Don't get fancy**, the point of this challenge is to learn about networking and HTTP, not crafting a perfect server.
