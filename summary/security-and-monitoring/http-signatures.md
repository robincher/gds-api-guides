---
description: HTTP Signature for API Authentication
---

# HTTP Signatures

Using HTTP Signatures is one of the most common method of providing authentication information. API authentication protects the sender, receiver and the message itself. It is important that the API is secured enough that a third party couldn't pose as the sender, receiver or modify the message content.

The goal for HTTP Signatures are to :

1.     **Verification of the requester's identity** - Identity of the API client is important in ensuring it is only consuming APIs it entitled to, and providing **accountability** for the system's access control.

2.     **In-transit Data Protection** - Protect against data tampering while the request is in transits.

APEX supports the following HTTP Signature Scheme for authentication

·         HMAC256 Authentication

·         RSA256 Authentication  

**General Rule of Thumb**

·         For APIs published in **Intranet**, minimally adopt **HMAC256 Signature**

·         For APIs published in **Internet**, minimally adopt **RSA256 Signature**

**Public Code Libraries for Forming APEX-based HTTP Signature**

·         Node.js Library - [https://github.com/GovTechSG/node-apex-api-security](https://github.com/GovTechSG/node-apex-api-security)

·         C\# Library - [https://github.com/GovTechSG/csharp-apex-api-security](https://github.com/GovTechSG/csharp-apex-api-security)

·         Java Library - [https://github.com/GovTechSG/java-apex-api-security](https://github.com/GovTechSG/java-apex-api-security)

·         and more to come..  


