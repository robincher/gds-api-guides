---
description: Using the right HTTP Response Code for your API
---

# HTTP Response Code

Every API designed should use standard HTTP response code to represent whether a specific [HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP) request operation has been successfully completed and communicate error to the clients.

| **CATEGORY** | **DESCRIPTION** |
| --- | --- | --- | --- | --- | --- |
| **1xx: Informational**        | Communicates transfer protocol-level information. |
| **2xx: Success** | Indicates that the client’s request was accepted successfully. |
| **3xx: Redirection**         | Indicates that the client must take some additional action in order to complete their request. |
| **4xx: Client Error** | Error caused by the client |
| **5xx: Server Error** | Error originated from the server |

Read more at  ["Common" HTTP Status Code](https://github.com/for-GET/know-your-http-well/blob/master/status-codes.md#common) for the codes description, and get familiar with their semantics.  


### Example \(Communicating an API Error\)

A request to get user 1234 :

```text
GET /users/1234 HTTP/1.1...
```

User 1234  is not found  

```text
HTTP/1.1 404 Not Found...
```

