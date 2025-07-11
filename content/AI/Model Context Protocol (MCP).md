---
title: MCP
tags:
  - AI
---
- Model Context Protocol
- a standard protocal to connect tools and context to AI applications (like a USB port of AI apps)
- custom integrations of your choice

Architecture (client-server architecture)
- MCP host (e.g. cursor) who start a MCP client process
- MCP client makes a request to the MCP server, and receive response
- MCP servers
	- Prompt
	- resrouce interaction
	- Tool (function, api, image processing)
## 1. **MCP Client**

### 🔹 What it is:

The **MCP client** is the part that interacts with the LLM (e.g., GPT) directly.
### 🔹 Responsibilities:

- Sends the **model** a **tool manifest** (i.e., what tools are available and how to use them).
- Receives tool calls from the model and **forwards them to the MCP server**.
- For example:
    - “Here's a `weather` tool. You can call `get_weather(location)`.”
    - If the model then decides to call `get_weather("London")`, the client forwards this to the MCP server.

## 2. **MCP Server**

### 🔹 What it is:

The **MCP server** is a proxy or translator that connects the model's tool calls to **real external services/APIs**.
### 🔹 Responsibilities:

- Accepts tool invocation requests from the MCP client.
- Maps those requests to **actual HTTP calls** to the external service.
- May also validate inputs, authenticate, or enrich the request.

Steps:
1. Client fetches tools from MCP server and stores them
2. User enters prompt
3. Client sends prompt + tools list to LLM
4. LLM responds with tool call(s) and arguments
5. Client sends tool call(s) to MCP server
6. MCP server invokes real external service
7. Response returns to client → to LLM
8. LLM generates final answer for the user