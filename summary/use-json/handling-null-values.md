---
description: Null Values in JSON
---

# Handling Null Values

Boolean attribute **must not be presented as nulls**. A boolean is essentially a closed enumeration of two values, true and false.

To full subscribe to OpenAPI 3.0 specification, attributes should be omitted if it is giving a null value. However that doesn’t prevent clients and servers sending and receiving those fields with null values

