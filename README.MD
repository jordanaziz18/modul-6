
## Commit 1 Reflection Notes

Here, in this very first example, I've coded a simple web server in Rust which listens at the localhost address (`127.0.0.1`) at port `7878`, accepts TCP connections, reads the HTTP request of every connection, and prints it to the console. The code uses Rust's standard library to create a TCP listener that accepts incoming connections, process incoming streams, read HTTP request data line by line until it reaches an empty line, and print the raw HTTP request for debugging purposes. The code in this initial version reads the request only and does not parse the request method, path, or headers yet, send any HTTP responses, or serve any content to the client.




## Commit 2 Reflection Notes

<img src="asset/image/TEstimage.png " width="750" height="500" alt="View result tree">

In this update, I've enhanced the web server to not just read HTTP requests but also respond to them properly. Now the server sends back a complete HTTP response with a status line, appropriate headers like Content-Length, and actual HTML content. The code reads an HTML file from the filesystem and serves it to the browser, allowing users to see a rendered webpage instead of just having their requests logged on the server side. This implementation follows standard HTTP protocol structure with proper response formatting including status codes, headers, and body content.

## Commit 3 reflection notes
<img src="asset/image/oops.png " width="750" height="500" alt="View result tree">

- Splitting the Response Handling
In order to do selective responding, we're going to check the first line of the HTTP request, rather than reading in the entire request as a vector, we invoke next to grab the first thing in the iterator. This is stored to the request_line variable, and if it's a GET request on a / path, then we return hello.html's contents. If we don't, we would have received some other request, so we'll add an else block to direct it into 404.html.

- Refactoring
If we examine the code, we can clearly notice that a lot of duplication is going on. We can optimize the code so that it's more streamlined by defining the status line and filename initially and using them later on. The if and else blocks now simply return the status line and filename, which are assigned to a tuple using the let statement. The resulting code is easier to maintain, since if we ever need to change anything to it, we must do so just once.


## commit 4 reflection notes

In this update, I added a /sleep route that delays response by 10 seconds to simulate slow operations. Testing with multiple browser tabs revealed that all requests get queued behind the slow one, demonstrating a key limitation of single-threaded servers. This exercise highlights why real-world web servers need multi-threading or asynchronous processing to handle multiple users efficiently.
