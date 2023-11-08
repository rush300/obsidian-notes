The HTTP headers are used to pass additional information between the client and the server through the request and responses headers.
All the headers are case-insensitive, headers fields are separated by colon, key-value pairs in clear text string format.

There are four kinds of headers context-wise:
* ==General Headers==: This type of headers applied on Request and Response headers both but without affecting the database body.
* ==Request Headers==: This type of headers contains information about the fetched request by the client
* ==Response Headers==: This type of headers contains the location of the source that has been requested by the client.
* ==Entity Headers==: This type of headers contains the information about the body of the resources like MIME type, Content-length.


