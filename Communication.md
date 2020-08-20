# Communication

## Ajax Polling:

- Client makes a request to the server at regular intervals (or maybe exponential backoff)
- Lots of http overhead since many responses could be empty if no updates have occurred

## HTTP Long-Polling:

- Client makes request to the server but the server doesn't reply immediately (sometimes called a Hanging GET)
- Server waits until some data becomes available to send a response instead of sending empty responses
- When the server finally does response the client sends another re-request immediately

## WebSockets:

- Full Duplex communication channel over TCP
- Handshake to establish the connection

## Server-Sent Events (SSEs)

- One way connection from the server to the client
- Client cannot send data to the server, it only makes the initial request

## MQTT (RabbitMQ)

- Pub / Sub messaging protocol over TCP
- messages sit in a queue until handled