
https://youtu.be/_CCyMWSZNU4?si=4ylv-huyk4KEQdcq

Real time communication

usecase-chat, stocks when real time dashboard showing KPIs

# Long Polling

**Interview Notes:**
- Client sends a request to the server and waits for a response.
- If no new data, server holds the request until data is available or timeout occurs.
- After response, client immediately sends a new request.
- Works with standard HTTP; easy to implement.
- Higher latency and increased server load due to repeated requests.

**System Design Explanation:**
- Useful when WebSockets are not supported.
- Scales poorly for large numbers of clients.
- Suitable for simple real-time updates (e.g., notifications).

**Pseudo Code:**
```pseudo
loop:
    sendRequestToServer()
    waitForResponse()
    if responseReceived:
        processData(response)
    repeat
```

# Server Sent Events (SSE)

**Interview Notes:**
- Unidirectional communication: server pushes updates to client over HTTP.
- Uses EventSource API in browsers.
- Lightweight compared to WebSockets for one-way data.
- Automatic reconnection and simple implementation.

**System Design Explanation:**
- Ideal for live feeds, dashboards, or notifications.
- Not suitable for bidirectional communication.
- Limited browser support (no IE).

**Pseudo Code:**
```pseudo
// Client-side
eventSource = new EventSource('/events')
eventSource.onmessage = function(event):
    processData(event.data)

// Server-side
while true:
    if newDataAvailable:
        sendEventToClients(data)
```

# WebSockets

**Interview Notes:**
- Full-duplex, bidirectional communication over a single TCP connection.
- Persistent connection; low latency.
- Suitable for chat apps, games, collaborative tools.
- Requires WebSocket protocol support on server and client.

**System Design Explanation:**
- Scales well for many concurrent connections.
- Efficient for real-time, interactive applications.
- Needs careful handling of connection lifecycle and security.
- Can be combined with message brokers for scalability.

**Pseudo Code:**
```pseudo
// Client-side
socket = new WebSocket('ws://server')
socket.onmessage = function(event):
    processData(event.data)
socket.send(message)

// Server-side
onConnection(socket):
    while socketOpen:
        if messageReceived:
            processMessage(message)
        if newDataAvailable:
            socket.send(data)
```

