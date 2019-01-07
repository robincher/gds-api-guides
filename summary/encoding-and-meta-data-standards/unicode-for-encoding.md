---
description: Use user-friendly character set
---

# Unicode for Encoding

To simplify encoding of resource IDs in URLs and parameters in the JSON payload, their representation must only consist of readable strings of letters, numbers, underscore, minus and colon. 

We recommend all to adopt [**UTF-8**](https://tools.ietf.org/html/rfc3629) ****as the default encoding standard for your APIs, to be align with widely adopted practice for modern web development.

A Unicode-based encoding such as UTF-8 can support many languages and can accommodate pages and forms in any mixture of those languages.Additionally, it allows many more languages to be mixed on a single page than any other choice of encoding

