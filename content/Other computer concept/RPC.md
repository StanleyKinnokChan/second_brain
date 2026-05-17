---
title: RPC
tags:
  - concepts
---
**RPC interface** stands for **Remote Procedure Call interface**. It's a way for software to execute a function or procedure on another computer (usually over a network), as if it were a local function.

### Breakdown:

- **Remote**: The function runs on another system.
- **Procedure Call**: It's like calling a function/method in your local code.
- **Interface**: A defined way (usually via protocol or API) to make the call.

### Example Use:

If App A wants to get data from Server B:

- App A calls a function like `getUser(123)` via RPC.
- Server B runs that function and sends the result back.
- App A continues as if it called the function locally.

### Common Technologies:

- **gRPC** (Google's RPC framework using HTTP/2)
- **JSON-RPC**, **XML-RPC**
- **Thrift** (by Apache)

### Key Features:

- Abstracts the network communication
- Can be synchronous or asynchronous
- Often used in microservices or distributed systems

It’s similar in concept to REST APIs, but more tightly coupled and structured like direct function calls.