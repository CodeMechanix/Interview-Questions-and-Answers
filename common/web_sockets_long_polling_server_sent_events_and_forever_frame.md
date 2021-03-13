### Question
What is the difference between web sockets, long polling, server-sent events and forever frame?

### Answer
1. WebSocket Full-duplex

Websocket is a full-duplex communication channels over a single TCP connection. When both server and browser support, it is the only transport that establishes a true persistent, two-way connection between client and server.

2. Server Sent Events Simplex

Also known as EventSource is a technology where a browser receives automatic updates from a server via HTTP connection. The Server-Sent Events EventSource API is standardized as part of HTML5 by the W3C.

3. Forever Frame One request -> One infinite response

Forever Frame creates a hidden IFrame which makes a request to an endpoint on the server that does not complete. The server then continually sends script to the client which is immediately executed, providing a one-way realtime connection from server to client. The connection from client to server uses a separate connection from the server to client connection, and like a standard HTTP request, a new connection is created for each piece of data that needs to be sent.

4. Ajax long polling (One Request -> One Response [but delayed]) repeated

Long polling does not create a persistent connection, but instead polls the server with a request that stays open until the server responds, at which point the connection closes, and a new connection is requested immediately. This may introduce some latency while the connection resets.

More To Know:
1. [Polling vs SSE vs WebSocket— How to choose the right one?](https://codeburst.io/polling-vs-sse-vs-websocket-how-to-choose-the-right-one-1859e4e13bd9)