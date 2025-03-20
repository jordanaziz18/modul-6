
# 1
### Commit 1 Reflection Notes

Here, in this very first example, I've coded a simple web server in Rust which listens at the localhost address (`127.0.0.1`) at port `7878`, accepts TCP connections, reads the HTTP request of every connection, and prints it to the console. The code uses Rust's standard library to create a TCP listener that accepts incoming connections, process incoming streams, read HTTP request data line by line until it reaches an empty line, and print the raw HTTP request for debugging purposes. The code in this initial version reads the request only and does not parse the request method, path, or headers yet, send any HTTP responses, or serve any content to the client.




# 2
### Commit 2 Reflection Notes

<img src="asset/image/TEstimage.png " width="750" height="500" alt="View result tree">

In this update, I've enhanced the web server to not just read HTTP requests but also respond to them properly. Now the server sends back a complete HTTP response with a status line, appropriate headers like Content-Length, and actual HTML content. The code reads an HTML file from the filesystem and serves it to the browser, allowing users to see a rendered webpage instead of just having their requests logged on the server side. This implementation follows standard HTTP protocol structure with proper response formatting including status codes, headers, and body content.
