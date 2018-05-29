---
description: Use RESTful for web-based API
---

# Use RESTful

As much as possible, follow the widely adopted industry's standard and where appropriate design your digital services, or api, using **REST,** an architecture standard based on HTTP.

**What is REST?**

Abstracted from [OSWAP](https://www.owasp.org/index.php/REST_Security_Cheat_Sheet) :

_The key abstraction of information in **REST** is a resource. A REST API resource is identified by a URI, usually a HTTP URL. REST components use connectors to perform actions on a resource by using a representation to capture the current or intended state of the resource and transferring that representation. The primary connector types are client and server, secondary connectors include cache, resolver and tunnel. In order to implement flows with REST APIs, resources are typically created, read, updated and deleted._

R. As compared to traditional SOA integration which focus more on operations that are use-case specific, REST is centered around business entities exposed as resources , and can be manipulate with standardized CRUD-like methods.

* We prefer REST-based APIs with [JSON payloads](use-json.md)
* We prefer new systems to be built with REST

In some cases, it may not be applicable to build a REST API, for example, when you are building an API to stream data or required the message to be persistent.





